# Food Order Management System Backend

REST API backend for a food ordering platform with authentication, role-based access, menu and category management, cart and order flow, payments, reviews, and user profile and admin features.

## Tech Stack

- Node.js
- Express.js
- MongoDB (Mongoose)
- JWT authentication
- Multer (memory storage for uploads)
- Cloudinary (image hosting)

## Project Structure

```text
backend/
  src/
    app.js
    server.js
    config/
      db.js
      cloudinary.js
    controllers/
    middleware/
    models/
    routes/
    seeder/
      createAdmin.js
    utils/
  package.json
  README.md
```

## Prerequisites

- Node.js 18+
- npm 9+
- MongoDB connection string
- Cloudinary account (for image uploads)

## Quick Start

1. Install dependencies.

```bash
npm install
```

2. Create `.env` in the project root with the variables below.

3. Start development server.

```bash
npm run dev
```

4. For production run.

```bash
npm start
```

By default, the API runs at `http://localhost:5000`.

## Environment Variables

Create `.env` in the project root:

```env
PORT=5000
NODE_ENV=development

MONGO_URI=your_mongodb_connection_string

JWT_SECRET=your_super_secret_key
JWT_EXPIRES_IN=7d

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
```

## API Base URL

- Local: `http://localhost:5000`
- API root: `/api`
- Health check: `GET /`

## Authentication

Protected endpoints require:

```http
Authorization: Bearer <jwt_token>
```

Role-restricted endpoints additionally require `admin` authorization.

## Main API Endpoints

### Auth (`/api/auth`)

- `POST /register`
- `POST /login`
- `GET /me` (protected)
- `GET /admin-only` (protected + admin)

### Categories (`/api/categories`)

- `GET /`
- `POST /` (admin)
- `GET /:id`
- `PUT /:id` (admin)
- `DELETE /:id` (admin)

### Menu (`/api/menu`)

- `GET /`
- `POST /` (admin, multipart image: `image`)
- `GET /:id`
- `PUT /:id` (admin, multipart image: `image`)
- `DELETE /:id` (admin)

### Orders (`/api/orders`)

- `GET /cart` (protected)
- `POST /cart` (protected)
- `DELETE /cart` (protected)
- `PUT /cart/:menuItemId` (protected)
- `DELETE /cart/:menuItemId` (protected)
- `GET /my-orders` (protected)
- `POST /` (protected, place order)
- `GET /` (admin, all orders)
- `GET /:id` (protected)
- `PATCH /:id/status` (admin)

### Payments (`/api/payments`)

- `POST /` (protected)
- `GET /` (admin)
- `GET /my-payments` (protected)
- `GET /:id` (protected)
- `PATCH /:id/status` (admin)

### Reviews (`/api/reviews`)

- `POST /` (protected)
- `GET /my-reviews` (protected)
- `GET /menu/:menuItemId`
- `PUT /:id` (protected)
- `DELETE /:id` (protected)

### Users (`/api/users`)

- `GET /profile` (protected)
- `PUT /profile` (protected, multipart image: `profileImage`)
- `GET /` (admin)
- `GET /:id` (admin)
- `PUT /:id` (admin, multipart image: `profileImage`)
- `DELETE /:id` (admin)
- `PATCH /:id/role` (admin)

## Admin Seeder

Create or update the admin user:

```bash
npm run seed:admin
```

The default credentials are currently defined in `src/seeder/createAdmin.js`.

Security note:

- Do not use hardcoded default credentials in production.
- Rotate admin credentials before first deployment.

## Scripts

- `npm run dev`: run with nodemon
- `npm start`: run with node
- `npm run seed:admin`: create or update admin user

## Error Response Pattern

Errors are returned in JSON format:

```json
{
  "success": false,
  "message": "Error message",
  "stack": "..."
}
```

`stack` is hidden in production mode.
