# MongoDB


## 🔹 1. What is MongoDB?
👉 MongoDB is a database that stores data in flexible JSON-like format instead of tables.
* MongoDB is a **NoSQL database**
* Stores data in **JSON-like format (BSON)**
* Used in modern apps (web, mobile, startups)
  
## 🔹 Key Points
📦 Stores data in collections (like tables)
📄 Each record is a document (like a JSON object)
⚡ No fixed structure (schema is flexible)
🚀 Fast and easy to use with modern apps
💻 Works well with JavaScript & Node.js

---

## 🔹 2. Basic Terms

| Term       | Meaning                  |
| ---------- | ------------------------ |
| Database   | Collection of data       |
| Collection | Like a table             |
| Document   | Like a row (JSON object) |

Example document:

```json
{
  "name": "Coffee",
  "price": 100
}
```

---

## 🔹 3. Why Use MongoDB? 👍

* Flexible schema (no fixed structure)
* Easy to scale
* Fast for web apps
* Works well with JavaScript

---

## 🔹 4. CRUD Operations (MOST IMPORTANT 🔥)

### ✅ Create

```js
db.menu.insertOne({ name: "Coffee", price: 100 });
```

---

### ✅ Read

```js
db.menu.find();
db.menu.find({ price: 100 });
```

---

### ✅ Update

```js
db.menu.updateOne(
  { name: "Coffee" },
  { $set: { price: 120 } }
);
```

---

### ✅ Delete

```js
db.menu.deleteOne({ name: "Coffee" });
```

---

## 🔹 5. Query Operators

* `$gt` → greater than
* `$lt` → less than
* `$in` → match values
* `$and`, `$or`

Example:

```js
db.menu.find({ price: { $gt: 100 } });
```

---

## 🔹 6. Indexes

* Speed up search queries

```js
db.menu.createIndex({ price: 1 });
```

---

## 🔹 7. Relationships (Important Concept)

MongoDB uses:

### 1. Embedding

```json
{
  "order_id": 1,
  "items": [
    { "name": "Coffee", "qty": 2 }
  ]
}
```

### 2. Referencing

```json
{
  "user_id": "123",
  "menu_id": "456"
}
```

---

## 🔹 8. Aggregation (Used in Jobs 📊)

Used for reports & analytics

```js
db.orders.aggregate([
  { $group: { _id: "$user_id", total: { $sum: "$amount" } } }
]);
```

---

## 🔹 9. Schema Design Tips

* Keep related data together (embedding)
* Avoid too many joins
* Keep documents small

---

## 🔹 10. Mongoose (Important for Developers)

* Mongoose helps use MongoDB in Node.js

Example:

```js
const mongoose = require("mongoose");

const UserSchema = new mongoose.Schema({
  name: String,
  email: String
});
```

---

## 🔹 11. Transactions

* Used for multiple operations safely
* Example: placing an order + payment

---

## 🔹 12. Security

* Use authentication
* Don’t expose database publicly
* Use roles & permissions

---

## 🔹 13. Deployment

* Use cloud DB: MongoDB Atlas
* Easy to connect with apps

---

## 🔹 14. Real-Life Uses

* E-commerce (orders, products)
* Social media apps
* Food delivery apps
* Chat applications

---

