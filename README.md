# 🍲 Recipes Management API — Backend Service

A scalable and modular **Node.js RESTful API** designed for managing culinary recipes. Built with **Express** and **MongoDB**, this backend service provides robust CRUD functionality, efficient schema modeling, dynamic query capabilities, and structured data persistence.

🔗 **Repository:** [https://github.com/titirot/recipes-backend-service](https://github.com/titirot/recipes-backend-service)

---

## 🛠️ Tech Stack & Tools

- **Runtime Environment:** Node.js
- **Web Framework:** Express.js
- **Database:** MongoDB
- **ODM / Data Access:** Mongoose (Schema validation & data modeling)
- **API Testing:** Postman
- **Environment Management:** dotenv

---

## ✨ Key Features & Capabilities

- **🍲 Recipe Management (CRUD):** Full API suite to create, read, update, and delete recipes.
- **🔍 Advanced Querying:** Dynamic filtering, searching by ingredients or categories, and sorting.
- **🛡️ Data Validation:** Strict Mongoose models and schema constraints ensuring clean input data.
- **⚡ Error Handling:** Centralized Express middleware for unified error parsing and HTTP response status codes.
- **🧱 Layered Architecture:** Modular organization separating Controllers, Services, Models, and Route definitions.

---

## 📁 Project Structure

```text
recipes-management-api/
├── config/         # Database connection & env setup
├── controllers/    # Request handlers & logic execution
├── models/         # Mongoose schema definitions
├── routes/         # Express API endpoint routes
├── middleware/     # Custom error handlers & validation
├── app.js          # Express app entry point
└── package.json    # Project dependencies & scripts

## Roles
- `guest` - not authenticated
- `registered` - authenticated regular user
- `admin` - authenticated administrator

## API Table
| Method | URL | Role | Description |
|---|---|---|---|
| POST | `/api/users/register` | guest | Register new user |
| POST | `/api/users/login` | guest | Login and get JWT token |
| GET | `/api/users` | admin | Get all users |
| PATCH | `/api/users/:id/password` | self/admin | Update user password |
| DELETE | `/api/users/:id` | admin | Delete user |
| GET | `/api/recipes?search=&limit=&page=` | guest/registered/admin | Get recipes with text search and paging |
| GET | `/api/recipes/:code` | guest/registered/admin | Get recipe by recipe code |
| GET | `/api/recipes/by-preparation-time?maxMinutes=30` | guest/registered/admin | Get recipes up to max preparation time |
| POST | `/api/recipes` | registered/admin | Add recipe |
| PUT | `/api/recipes/:id` | recipe owner/admin* | Update recipe |
| DELETE | `/api/recipes/:id` | recipe owner/admin* | Delete recipe |
| GET | `/api/categories` | guest/registered/admin | Get all categories |
| GET | `/api/categories/with-recipes` | guest/registered/admin | Get all categories with recipes |
| GET | `/api/categories/lookup/:value` | guest/registered/admin | Get category by code/name with recipes |

\* Route role allows authenticated users; controller enforces ownership.

