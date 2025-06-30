Here's a complete **use case for using [k6](https://k6.io)** to load test **ASP.NET Core API endpoints**, including setup, writing a test script (`script.js`), and interpreting the results.

---

## ✅ Scenario: Load Testing an ASP.NET Core Web API

Assume you have an ASP.NET Core API running at:

```
https://localhost:5001/api/products
```

This API supports:

* `GET /api/products`
* `GET /api/products/{id}`
* `POST /api/products`
* `PUT /api/products/{id}`
* `DELETE /api/products/{id}`

---

## 🔧 Step 1: Install k6

Install [k6](https://k6.io/docs/getting-started/installation/) CLI:

### Mac:

```bash
brew install k6
```

### Windows (Chocolatey):

```bash
choco install k6
```

---

## 📜 Step 2: Create the `script.js` for Load Testing

```js
import http from 'k6/http';
import { check, sleep } from 'k6';

// Options: how many VUs (virtual users) and duration
export const options = {
  stages: [
    { duration: '10s', target: 10 }, // ramp-up to 10 users
    { duration: '30s', target: 10 }, // hold 10 users
    { duration: '10s', target: 0 },  // ramp-down to 0
  ],
};

const BASE_URL = 'https://localhost:5001/api/products';

export default function () {
  // 1. GET all products
  let res = http.get(BASE_URL);
  check(res, {
    'GET all products status is 200': (r) => r.status === 200,
  });

  // 2. GET single product (assuming ID 1 exists)
  res = http.get(`${BASE_URL}/1`);
  check(res, {
    'GET product 1 status is 200': (r) => r.status === 200,
  });

  // 3. POST new product
  const payload = JSON.stringify({
    name: `Test Product ${Math.random()}`,
    price: 99.99,
    stock: 10
  });

  res = http.post(BASE_URL, payload, {
    headers: { 'Content-Type': 'application/json' },
  });
  check(res, {
    'POST product status is 201': (r) => r.status === 201,
  });

  const createdProduct = res.json();
  const createdId = createdProduct.id;

  // 4. PUT update product
  const updatedPayload = JSON.stringify({
    id: createdId,
    name: 'Updated Product',
    price: 79.99,
    stock: 15,
  });

  res = http.put(`${BASE_URL}/${createdId}`, updatedPayload, {
    headers: { 'Content-Type': 'application/json' },
  });
  check(res, {
    'PUT product status is 204': (r) => r.status === 204,
  });

  // 5. DELETE product
  res = http.del(`${BASE_URL}/${createdId}`);
  check(res, {
    'DELETE product status is 204': (r) => r.status === 204,
  });

  sleep(1); // pause between iterations
}
```

---

## 🚀 Step 3: Run the Test

Make sure your ASP.NET Core API is running and accessible (use HTTPS, or allow insecure connections).

```bash
k6 run script.js
```

If using self-signed SSL certs in development, allow insecure:

```bash
k6 run --insecure-skip-tls-verify script.js
```

---

## 📈 Step 4: Analyze Output

After running, you'll get output like:

```
✓ GET all products status is 200
✓ GET product 1 status is 200
✓ POST product status is 201
✓ PUT product status is 204
✓ DELETE product status is 204

  checks.......................: 100.00% ✓ 50 ✗ 0
  http_req_duration............: avg=100ms min=80ms max=130ms
  http_reqs....................: 10
  vus..........................: 10
  iterations...................: 10
```

Use this to:

* Ensure your endpoints are reliable under load.
* Identify performance bottlenecks (e.g., high response times).

---

## 🧪 Optional: Add More Tests

You can test:

* Authentication headers (JWT, Basic Auth)
* Error responses (e.g., 404 or 500)
* Data validation (400 Bad Request)

Let me know if you want a version with **JWT token handling**, **data from file**, or **Test Summary JSON export**.


Great question — and you're absolutely right to ask. By default, **k6 shows aggregate metrics**, so it’s not always obvious *which specific API endpoint* is causing slowdowns or errors.

To **identify bottlenecks per endpoint**, you need to **tag and group requests**, so you can break down the metrics by API call.

---

## ✅ Step-by-Step: Identify Which Endpoint Is the Bottleneck

### 🔧 1. Use `group()` and `tags` in your `script.js`

```js
import http from 'k6/http';
import { check, sleep, group } from 'k6';

export const options = {
  stages: [
    { duration: '10s', target: 10 },
    { duration: '30s', target: 10 },
    { duration: '10s', target: 0 },
  ],
};

const BASE_URL = 'https://localhost:5001/api/products';

export default function () {
  group('GET all products', function () {
    const res = http.get(BASE_URL, { tags: { name: 'GET all' } });
    check(res, { 'status is 200': (r) => r.status === 200 });
  });

  group('GET product by ID', function () {
    const res = http.get(`${BASE_URL}/1`, { tags: { name: 'GET one' } });
    check(res, { 'status is 200': (r) => r.status === 200 });
  });

  group('POST product', function () {
    const payload = JSON.stringify({
      name: 'New Product',
      price: 10.99,
      stock: 100,
    });
    const res = http.post(BASE_URL, payload, {
      headers: { 'Content-Type': 'application/json' },
      tags: { name: 'POST product' },
    });
    check(res, { 'status is 201': (r) => r.status === 201 });
  });

  sleep(1);
}
```

---

### 📈 2. Run the test and look at breakdown using tags

```bash
k6 run script.js
```

Add `--summary-trend-stats` to control what metrics are shown:

```bash
k6 run --summary-trend-stats="avg,min,max,p(90),p(95),count" script.js
```

---

### 🧪 Example Output (Simulated)

```
http_req_duration{ name:GET all }.....: avg=45ms   min=40ms  max=60ms  p(90)=55ms p(95)=58ms
http_req_duration{ name:GET one }.....: avg=300ms  min=250ms max=500ms p(90)=450ms p(95)=490ms
http_req_duration{ name:POST product } : avg=120ms min=100ms max=300ms p(90)=290ms p(95)=295ms
```

### 🔍 How to interpret this:

* `GET one` endpoint is **much slower** (300ms avg, 500ms max) than others.
* That's your **bottleneck**.
* Look at your ASP.NET logs, SQL queries, and profiling for this endpoint.

---

### ✅ Optional: Output to JSON for deeper analysis

```bash
k6 run script.js --out json=results.json
```

Then analyze using tools like:

* [k6 Reporter](https://github.com/benc-uk/k6-reporter)
* Grafana + InfluxDB (advanced)

---

### 💡 Bonus Tip: Use `http_req_failed` to catch errors

k6 shows HTTP request failures separately. Look for:

```
http_req_failed.................: 0.00% ✓ 0 ✗ 100
```

If this is not 0%, investigate the endpoint where failures happen using your tags.

---

## ✅ Summary: How to Identify the Bottleneck

| Feature                      | What to Do                                  |
| ---------------------------- | ------------------------------------------- |
| **See slow endpoints**       | Use `tags` and check `http_req_duration`    |
| **Group logs by endpoint**   | Use `group()`                               |
| **Catch failures**           | Use `check()` and monitor `http_req_failed` |
| **Export for deep analysis** | Use `--out json=...` or Grafana             |

Let me know if you want a full version integrated with **Grafana dashboards**, **Postman test porting**, or **authentication tokens**!
