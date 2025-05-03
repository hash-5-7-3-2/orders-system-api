# 🧾 Orders System API

A MuleSoft-based RESTful API to manage customer orders — including full CRUD operations, validation, database integration (MySQL), error handling, and clean RAML documentation.

---

## 🚀 Features

- ✅ Create, read, update, and delete orders
- ✅ Input validation for required fields
- ✅ Global error handling (400, 404, 502, 500)
- ✅ RAML 1.0 API contract
- ✅ MySQL backend integration
- ✅ Clean modular flows in Mule 4

---

## 📦 Technologies Used

- MuleSoft Anypoint Studio (Mule 4)
- RAML 1.0
- MySQL
- DataWeave 2.0
- Maven

---

## 🗂️ Project Structure

```
orders-system-api/
├── src/
│   ├── main/
│   │   ├── mule/                  # Mule flows
│           └── orders-system-api.xml
│   │   └── resources/
│   │       ├── api/              # RAML files
│   │       └── config.properties # DB config
├── pom.xml
├── mule-artifact.json
├── .gitignore
└── README.md
```

---

## 📑 API Endpoints

### `GET /api/orders`
Returns all orders.

### `GET /api/orders/{order_id}`
Returns one order by ID.

### `POST /api/orders`
Creates a new order.  
**Required fields:** `customerId`, `orderTotal`  
_Optional:_ `status`

### `PUT /api/orders/{order_id}`
Updates an existing order.  
**Required fields:** `customerId`, `status`, `orderTotal`

### `DELETE /api/orders/{order_id}`
Deletes an order by ID.

---

## 🧪 Sample Requests & Responses

### ✅ Create Order (POST)
```json
{
  "customerId": 103,
  "status": "NEW",
  "orderTotal": 150.75
}
```

### ✅ Success Response
```json
{
  "success": true,
  "message": "Order created"
}
```

### ❌ Error Response
```json
{
  "error": "VALIDATION:BAD_REQUEST",
  "description": "customerId and orderTotal are required"
}
```

---

## 🛠️ Database Setup (MySQL)

```sql
CREATE TABLE Orders (
  order_id     INT AUTO_INCREMENT PRIMARY KEY,
  customer_id  INT NOT NULL,
  status       VARCHAR(20) NOT NULL,
  order_total  DECIMAL(10,2) NOT NULL,
  created_at   DATETIME DEFAULT CURRENT_TIMESTAMP
);

INSERT INTO Orders (customer_id, status, order_total)
VALUES (101, 'NEW', 199.99), (102, 'NEW', 49.50);
```

Update `config.properties` with your local DB connection:
```properties
db.host=dbhost
db.port=port
db.username=dbusername
db.password=yourpassword
db.name=dbname
```

---

## 🧰 How to Run

1. Clone this repo:
   ```bash
   git clone https://github.com/YOUR_USERNAME/orders-system-api.git
   ```

2. Open in Anypoint Studio

3. Make sure MySQL is running and DB is created

4. Update DB credentials in `config.properties`

5. Right-click project → Run as Mule Application

6. Test in Postman:
   ```
   http://localhost:8081/api/orders
   ```

---

## 🌐 Optional Cloud Deployment

This project can be deployed to CloudHub with minimal setup (JAR export or direct deploy from Studio).

---

## 👤 Anypoint Exchange

**RAML File**

Refer the documentation for more examples and api specs at: https://anypoint.mulesoft.com/exchange/ce58488b-0ced-4659-8121-bfaea748baf3/orders-system-api/minor/1.0/


---

## 📝 License

This project is licensed under the MIT License.
