# Product Inventory Management System - Quick Start Guide

## Prerequisites

- Node.js (v16+)
- PostgreSQL (v12+)
- Docker & Docker Compose (optional)
- Git

## Project Structure

```
product-inventory-system/
├── backend/              # Node.js + Express backend
├── frontend/             # React + Ant Design frontend
├── docker-compose.yml    # Docker Compose configuration
├── database/             # Database initialization scripts
└── README.md             # This file
```

## Installation

### Option 1: Docker Compose (Recommended)

```bash
# Clone the repository
git clone https://github.com/616932523-cell/product-inventory-system.git
cd product-inventory-system

# Start all services
docker-compose up -d

# Access the application
# Frontend: http://localhost:3001
# Backend API: http://localhost:3000
# Database: localhost:5432
```

### Option 2: Manual Installation

#### Backend Setup

```bash
cd backend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Update .env with your database connection
# DATABASE_URL=postgresql://user:password@localhost:5432/inventory_db

# Run database migrations
npm run migration:run

# Start the server
npm run dev
```

The backend will start on http://localhost:3000

#### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Update .env if needed
# REACT_APP_API_URL=http://localhost:3000/api

# Start the development server
npm start
```

The frontend will start on http://localhost:3000

## Default Login Credentials

- **Username**: admin
- **Password**: admin123

## API Documentation

### Authentication Endpoints

- `POST /api/auth/login` - User login
- `POST /api/auth/register` - User registration
- `GET /api/auth/me` - Get current user
- `POST /api/auth/logout` - Logout

### Product Endpoints

- `GET /api/products` - List products
- `GET /api/products/:id` - Get product details
- `POST /api/products` - Create product (Admin only)
- `PUT /api/products/:id` - Update product (Admin only)
- `DELETE /api/products/:id` - Delete product (Admin only)
- `GET /api/products/low-stock` - Get low stock products

### Inventory Endpoints

- `GET /api/inventory` - List inventory
- `GET /api/inventory/product/:productId` - Get product inventory
- `GET /api/inventory/low-stock` - Get low stock items
- `GET /api/inventory/summary` - Get inventory summary

### Inbound Orders

- `GET /api/inbound-orders` - List inbound orders
- `GET /api/inbound-orders/:id` - Get order details
- `POST /api/inbound-orders` - Create order (Warehouse only)
- `PUT /api/inbound-orders/:id` - Update order
- `PATCH /api/inbound-orders/:id/status` - Update order status
- `DELETE /api/inbound-orders/:id` - Delete order

### Outbound Orders

- `GET /api/outbound-orders` - List outbound orders
- `GET /api/outbound-orders/:id` - Get order details
- `POST /api/outbound-orders` - Create order (Sales only)
- `PUT /api/outbound-orders/:id` - Update order
- `PATCH /api/outbound-orders/:id/confirm` - Confirm order
- `PATCH /api/outbound-orders/:id/status` - Update order status
- `DELETE /api/outbound-orders/:id` - Delete order

## Features

- ✅ User authentication with JWT
- ✅ Role-based access control (Admin, Warehouse, Sales, User)
- ✅ Product catalog management
- ✅ Real-time inventory tracking
- ✅ Inbound order management
- ✅ Outbound order management
- ✅ Low stock alerts
- ✅ Profit calculation
- ✅ Audit logging
- ✅ Responsive UI with Ant Design
- ✅ Docker containerization
- ✅ GitHub Actions CI/CD

## Environment Variables

### Backend (.env)

```
NODE_ENV=development
PORT=3000
DATABASE_URL=postgresql://user:password@localhost:5432/inventory_db
JWT_SECRET=your-secret-key
JWT_EXPIRY=7d
CORS_ORIGIN=http://localhost:3000
```

### Frontend (.env)

```
REACT_APP_API_URL=http://localhost:3000/api
```

## Development

### Backend Development

```bash
cd backend

# Install dependencies
npm install

# Start development server with hot reload
npm run dev

# Run tests
npm run test

# Build for production
npm run build
```

### Frontend Development

```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm start

# Run tests
npm run test

# Build for production
npm run build
```

## Production Deployment

### Using Docker

```bash
# Build images
docker build -t inventory-backend:latest ./backend
docker build -t inventory-frontend:latest ./frontend

# Push to registry (Docker Hub, ECR, etc.)
docker push inventory-backend:latest
docker push inventory-frontend:latest

# Deploy using your preferred orchestration (Kubernetes, Docker Swarm, etc.)
```

### Manual Deployment

1. Build the applications:
   ```bash
   cd backend && npm run build
   cd ../frontend && npm run build
   ```

2. Deploy backend to your server
3. Deploy frontend static files to CDN or web server
4. Configure database and environment variables
5. Start services using process manager (PM2, systemd, etc.)

## Troubleshooting

### Database Connection Error

- Check PostgreSQL is running
- Verify DATABASE_URL is correct
- Ensure database exists and user has permissions

### Port Already in Use

- Change PORT in .env
- Or kill the process using the port: `lsof -i :3000`

### Frontend Can't Connect to Backend

- Verify backend is running on the correct port
- Check CORS_ORIGIN in backend .env matches frontend URL
- Check REACT_APP_API_URL in frontend .env

## Support

For issues and feature requests, please create an issue in the GitHub repository.

## License

MIT License - see LICENSE file for details.

## Contributors

- Your Name (2026)

---

**Happy Inventory Managing! 🎉**
