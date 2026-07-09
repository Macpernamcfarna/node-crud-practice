# node-crud-practice
"A lightweight, modular RESTful API built from scratch using Node.js, Express, and UUID for full CRUD operations on user data."
# 🚀 User Management RESTful API

A robust, production-ready RESTful API built from scratch utilizing **Node.js** and **Express.js**. This project features a completely decoupled architecture, implementing the **Controller-Router** design pattern (MVC-style separation of concerns) to handle core CRUD operations seamlessly on an in-memory database.

---

## 🏗️ Architecture & Data Flow

This API separates route definitions from the actual business logic to ensure maintainability, scalability, and clean testing boundaries. 

- **`index.js`**: The main entry point. Configures the Express application server, registers standard body-parsing middlewares, and hooks up base router prefixes.
- **`routes/`**: Acts as the gatekeeper. Maps specific HTTP methods (`GET`, `POST`, `PATCH`, `DELETE`) and URL string paths directly to their designated controllers.
- **`controllers/`**: The brain of the application. Contains isolated JavaScript functions handling state mutation, parsing request arguments, handling safety fallback errors, and dispatching JSON responses.

### Request Cycle Pipeline
```text
[Client Request] ──> [index.js (App Instance + express.json())] 
                            └──> [routes/users.js (Router Parameter Mapping)]
                                         └──> [controllers/users.js (Business Logic)]
```
🛠️ Tech Stack & Key Modules
Runtime: Node.js (v24.x)

Backend Framework: Express.js

Dynamic ID Generator: UUID v4 (Universally Unique Identifiers)

Process Watcher: Nodemon (Hot-reloading development server)

📂 Project Directory Layout
api_project/
├── controllers/
│   └── users.js         # Core business logic, error tracking & array filtration
├── routes/
│   └── users.js         # Endpoint path parameter mapping & HTTP verb assignment
├── index.js             # Server initializer, port binder & global middleware setup
├── package.json         # Directives blueprint, dependency manifest, and running scripts
├── package-lock.json    # Strict dependency lock tree tracking
└── .gitignore           # Safeguard configuration file hiding node_modules from Git
🚦 REST API Endpoints Matrix
All endpoints are relative to the base URL: http://localhost:5000/users

Method	Endpoint	Description	Payload (JSON)	Success Status
GET	/users	Fetch all users in the array data store	None	200 OK
POST	/users	Create a new user with an auto-assigned UUID	firstName, lastName, age	200 OK
GET	/users/:id	Fetch details of a single user by their unique ID	None	200 OK / 404
DELETE	/users/:id	Drop a specific user completely from data store	None	200 OK
PATCH	/users/:id	Dynamically update specific keys of a user	Optional firstName, lastName, age	200 OK / 404

📦 JSON Payload Formats
1. Creating a User (POST /users)
{
  "firstName": "Johnny",
  "lastName": "Doe",
  "age": 15
}
⚡ Local Setup & Execution Guide
Follow these sequential terminal commands to replicate the runtime environment on your local system.

1. Prerequisites
Ensure you have the latest long-term support version of Node.js installed on your workstation.

2. Dependency Ingestion
Clone the repository to your desktop, shift into the folder context, and ingest the module matrix:
npm install
💡 Note: Running this command instructs npm to cross-examine the uploaded package.json manifest blueprint, automatically fetching and configuring local instances of Express and UUID inside a generated node_modules/ folder.

3. Ignition
Launch the application shell using the pre-configured nodemon engine process:
npm run dev
Upon terminal output confirmation, access the server interface shell locally via:

plaintext
http://localhost:5000

