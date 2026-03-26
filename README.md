# Food Order Management System Backend

This backend is built with:

- Node.js
- Express.js
- MongoDB Atlas
- JWT authentication
- Multer
- Cloudinary

## Folder Structure

```text
backend/
  src/
    config/
      cloudinary.js
      db.js
    controllers/
      authController.js
      categoryController.js
      menuController.js
      orderController.js
      paymentController.js
      reviewController.js
      userController.js
    middleware/
      authMiddleware.js
      errorMiddleware.js
      uploadMiddleware.js
    models/
      Category.js
      MenuItem.js
      Order.js
      Payment.js
      Review.js
      User.js
    routes/
      authRoutes.js
      categoryRoutes.js
      menuRoutes.js
      orderRoutes.js
      paymentRoutes.js
      reviewRoutes.js
      userRoutes.js
    utils/
      cloudinaryUpload.js
      generateToken.js
      sanitizeUser.js
    seeder/
      createAdmin.js
    app.js
    server.js
  .env.example
  .gitignore
  package.json
```

## Run the Project

1. Create a `.env` file using `.env.example`
2. Install dependencies:

```bash
npm install
```

3. Start the server:

```bash
npm run dev
```

## Create First Admin

Set `ADMIN_NAME`, `ADMIN_EMAIL`, and `ADMIN_PASSWORD` in `.env`, then run:

```bash
npm run seed:admin
```

## Current API Modules

- Authentication
- Category Management
- Menu Management
- Order Management
- Payment Management
- Review System
- User Management
