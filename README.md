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

## 🚀 How to Run This API Locally Using Anypoint Studio & Prebuilt JAR

This project provides a ready-to-run `.jar` file that you can launch directly inside **Anypoint Studio**, even without importing the source code.

### ✅ Prerequisites

- Anypoint Studio 7.x (with Mule 4 runtime)
- Java 8+ installed
- Internet connection for dependencies (first run)

---

### 📥 Step 1: Download the JAR

Grab the latest compiled JAR file from this repository:

👉 [`orders-system-api-1.0.0.jar`](https://github.com/hash-5-7-3-2/orders-system-api/releases/download/v1/orders-system-api.jar)


---

### 🧪 Step 2: Place the JAR into the Mule Runtime App Directory

1. In Anypoint Studio, open the embedded **Mule Runtime installation folder**:
   - Example: `C:\AnypointStudio\mule-4.4.0\runtime\mule\apps`
2. Copy the downloaded `.jar` file into the `apps/` folder
3. Start the Mule Runtime:
   - From Studio: use the **Console → Local Mule Runtime → Start**
   - Or run from command line:
     ```bash
     ./mule
     ```

---

### 🌐 Step 3: Access the API

Once the runtime starts, your API will be accessible at:

```
http://localhost:8081/api/orders
```

You can now test the full CRUD flow using Postman, curl, or a browser (for GETs).

---

### 🛠 Remember to add your database configurations:

1. `config.properties` file under `mule/apps/orders-system-api/`
2. Add your DB details:
   ```properties
   db.host=dbhost
   db.port=dbport
   db.username=dbusername
   db.password=dbpassword
   db.name=dbname
   ```

---

## 👤 Anypoint Exchange

**RAML File**

Refer the documentation for more examples and api specs at: https://anypoint.mulesoft.com/exchange/ce58488b-0ced-4659-8121-bfaea748baf3/orders-system-api/minor/1.0/


---

## 📝 License

This project is licensed under the MIT License.
