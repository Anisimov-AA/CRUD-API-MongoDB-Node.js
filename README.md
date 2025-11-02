RESTful API with full CRUD operations for product management using **Express.js** and **MongoDB**.
- **Separation of concerns** - routes -> controllers -> models (clean MVC)
- **Mongoose validation** - enforces required fields and defaults at schema level
- **RESTful conventions** - proper HTTP methods (POST/GET/PUT/DELETE) and status codes
- **Timestamps** - automatic `createdAt` and `updatedAt` fields
- **Nodemon for dev** - auto-reload on file changes with `npm run dev`

## Setup

**Requirements:** Node.js, MongoDB

1. install dependencies
```bash
npm install
```

2. run development server
```bash
npm run dev
```

Server runs at `http://localhost:3000`

## API Endpoints

**Base URL:** `http://localhost:3000/api/products`

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST   | `/`      | Create new product |
| GET    | `/`      | Get all products |
| GET    | `/:id`   | Get product by ID |
| PUT    | `/:id`   | Update product |
| DELETE | `/:id`   | Delete product |

## Usage

**Product Schema:**
```json
{
  "name": "string (required)",
  "quantity": "number (default: 0)",
  "price": "number (default: 0)",
  "image": "string (optional)"
}
```

**Create Product:**
```bash
curl -X POST http://localhost:3000/api/products \
  -H "Content-Type: application/json" \
  -d '{
    "name": "iPhone 15",
    "quantity": 10,
    "price": 999.99
  }'
```

**Get All Products:**
```bash
curl http://localhost:3000/api/products
```

**Get Product by ID:**
```bash
curl http://localhost:3000/api/products/:id
```

**Update Product:**
```bash
curl -X PUT http://localhost:3000/api/products/:id \
  -H "Content-Type: application/json" \
  -d '{"price": 1099.99}'
```

**Delete Product:**
```bash
curl -X DELETE http://localhost:3000/api/products/:id
```

## Architecture
```
project/
├── models/
│   └── product.model.js       # Mongoose schema with validation
├── controllers/
│   └── product.controller.js  # CRUD logic (create, read, update, delete)
├── routes/
│   └── product.route.js       # express router endpoint definitions
├── index.js                   # entry point, MongoDB connection
├── package.json
└── .gitignore
```
