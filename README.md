# Farmer's Market E-Commerce Platform

This project is an e-commerce platform designed to connect farmers directly with consumers. It facilitates the sale of agricultural products, allowing farmers to showcase their produce and consumers to purchase fresh, locally-sourced items.

## Features

- **User Authentication**: Separate registration and login for farmers and consumers.
- **Product Management**: Farmers can create, update, and delete product listings.
- **Order System**: Consumers can place orders, and farmers can manage received orders.
- **Review and Rating**: Consumers can leave comments and ratings for farmers and products.
- **User Profiles**: Both farmers and consumers have customizable profiles.
- **Shopping Cart**: Consumers can add products to their cart before checkout.
- **Search and Filter**: Users can search for products and filter by categories.
- **Follow System**: Consumers can follow their favorite farmers.

## Tech Stack

- Backend: Node.js with Express.js
- Database: [Your database choice, e.g., MongoDB, PostgreSQL]
- Authentication: JSON Web Tokens (JWT)
- File Upload: Multer middleware

## Project Structure

The project follows a modular structure with separate routes for different functionalities:

- `routes/auth.ts`: Handles user authentication and registration
- `routes/products.ts`: Manages product-related operations
- `routes/farmers.ts`: Handles farmer-specific routes
- `routes/consumers.ts`: Manages consumer-specific functionalities
- `routes/orders.ts`: Deals with order placement and management
- `routes/comments.ts`: Handles the comment system

## Setup and Installation
npm install

1. Clone the repository:
   ```
   git clone https://github.com/your-username/farmers-market-platform.git
   ```

2. Install dependencies:
   ```
   cd farmers-market-platform
   npm install
   ```

3. Set up environment variables:
   Create a `.env` file in the root directory and add the following:
   ```
   PORT=3000
   MONGODB_URI=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret
   ```

4. Start the server:
   ```
   npm start
   ```

## API Documentation

API Documentation
Authentication
Login
URL: /auth/login
Method: POST
Description: Authenticate a user and return a token.
Register Farmer
URL: /auth/register/farmer
Method: POST
Description: Register a new farmer account.
Middleware: uploadFileMiddleware.single('image')
Register Consumer
URL: /auth/register/consumer
Method: POST
Description: Register a new consumer account.
Middleware: uploadFileMiddleware.single('image')
Check Email Existence
URL: /auth/userExists/email/:email
Method: GET
Description: Check if an email is already registered.
Check Username Existence
URL: /auth/userExists/name/:name
Method: GET
Description: Check if a username is already taken.
Get User Profile
URL: /auth
Method: GET
Description: Retrieve the authenticated user's profile information.
Middleware: authenticateMiddleware
Products
Get All Products
URL: /products
Method: GET
Description: Retrieve all products.
Create Product
URL: /products
Method: POST
Description: Create a new product (farmer only).
Middleware: authenticateMiddleware, authorizeFarmer, uploadFileMiddleware.single('images')
Get Top Rated Products
URL: /products/topRatedProducts
Method: GET
Description: Retrieve top-rated products.
Get Discounted Products
URL: /products/discountedProducts
Method: GET
Description: Retrieve products with discounts.
Get Products from Last 30 Days
URL: /products/lastThirtyDayProducts/:farmerID
Method: GET
Description: Retrieve products added in the last 30 days for a specific farmer.
Get Product Details
URL: /products/:productID
Method: GET
Description: Retrieve details of a specific product.
Update Product
URL: /products/:productID
Method: PATCH
Description: Update a product (farmer only).
Middleware: authenticateMiddleware, uploadFileMiddleware.single('images')
Delete Product
URL: /products/:productID
Method: DELETE
Description: Delete a product (farmer only).
Middleware: authenticateMiddleware, authorizeFarmer
Get Products by Category
URL: /products/category/:parentCategory
Method: GET
Description: Retrieve products of a specific category.
Farmers
Get Farmer's Products
URL: /farmers/:farmerID/products
Method: GET
Description: Retrieve all products of a specific farmer.
Add Comments to Farmer
URL: /farmers/:farmerID/comments
Method: PATCH
Description: Add a comment to a farmer's profile (consumer only).
Middleware: authenticateMiddleware, authorizeConsumer
Get Farmer Details
URL: /farmers/:farmerID
Method: GET
Description: Retrieve details of a specific farmer.
Update Farmer Profile
URL: /farmers
Method: PATCH
Description: Update farmer's profile (farmer only).
Middleware: authenticateMiddleware, authorizeFarmer, uploadFileMiddleware.single('image')
Consumers
Get Shopping Cart
URL: /consumers/shoppingCart
Method: GET
Description: Retrieve the consumer's shopping cart.
Middleware: authMiddleware, authorizeConsumer
Follow Farmer
URL: /consumers/followFarmer
Method: PATCH
Description: Follow a farmer.
Middleware: authMiddleware, authorizeConsumer
Unfollow Farmer
URL: /consumers/unFollowFarmer
Method: PATCH
Description: Unfollow a farmer.
Middleware: authMiddleware, authorizeConsumer
Get Consumer Details
URL: /consumers/:consumerID
Method: GET
Description: Retrieve details of a specific consumer (farmer only).
Middleware: authMiddleware, authorizeFarmer
Update Consumer Profile
URL: /consumers
Method: PATCH
Description: Update consumer's profile (consumer only).
Middleware: authMiddleware, authorizeConsumer, uploadFileMiddleware.single('image')
Orders
Get Orders
URL: /orders
Method: GET
Description: Retrieve orders for the authenticated user.
Middleware: authenticateMiddleware
Add Order
URL: /orders
Method: POST
Description: Place a new order (consumer only).
Middleware: authenticateMiddleware, authorizeConsumer
Get Orders to Review
URL: /orders/reviewOrders
Method: GET
Description: Retrieve orders that can be reviewed (consumer only).
Middleware: authenticateMiddleware, authorizeConsumer
Get Orders by Date
URL: /orders/date/:date
Method: GET
Description: Retrieve orders for a specific date (farmer only).
Middleware: authenticateMiddleware, authorizeFarmer
Update Order
URL: /orders/:orderID
Method: PATCH
Description: Update an order.
Middleware: authenticateMiddleware
Delete Order
URL: /orders/:orderID
Method: DELETE
Description: Delete an order (farmer only).
Middleware: authenticateMiddleware, authorizeFarmer
Comments
Get Number of Comments for Farmer
URL: /comments/farmer/:farmerID/count
Method: GET
Description: Get the number of comments for a specific farmer.
Get Comments for Farmer
URL: /comments/farmer/:farmerID
Method: GET
Description: Get all comments for a specific farmer.
Get Number of Comments for Product
URL: /comments/product/:productID/count
Method: GET
Description: Get the number of comments for a specific product.
Get Comments for Product
URL: /comments/product/:productID
Method: GET
Description: Get all comments for a specific product.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
