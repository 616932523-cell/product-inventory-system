# Product Inventory Management System

## Overview
A comprehensive web-based inventory management system for tracking product inbound/outbound orders, stock management, supplier and customer relationships, with advanced reporting and analytics features.

## Technology Stack

### Backend
- **Runtime**: Node.js + TypeScript
- **Framework**: Express.js
- **Database**: PostgreSQL
- **ORM**: TypeORM
- **Authentication**: JWT (JSON Web Tokens)
- **Password Hashing**: bcryptjs

### Frontend
- **Framework**: React 18 + TypeScript
- **UI Library**: Ant Design Pro
- **State Management**: Redux Toolkit
- **HTTP Client**: Axios
- **Routing**: React Router v6

### DevOps
- **Containerization**: Docker & Docker Compose
- **CI/CD**: GitHub Actions
- **Package Manager**: npm / yarn

## Project Structure

```
product-inventory-system/
├── backend/
│   ├── src/
│   │   ├── entities/          # TypeORM entities
│   │   ├── services/          # Business logic
│   │   ├── routes/            # API routes
│   │   ├── middleware/        # Express middleware
│   │   ├── database.ts        # Database configuration
│   │   └── index.ts           # Application entry point
│   ├── package.json
│   ├── tsconfig.json
│   └── Dockerfile
├── frontend/
│   ├── src/
│   │   ├── components/        # React components
│   │   ├── pages/             # Page components
│   │   ├── services/          # API services
│   │   ├── store/             # Redux store
│   │   └── App.tsx            # Root component
│   ├── package.json
│   └── Dockerfile
├── docker-compose.yml
├── .github/
│   └── workflows/             # CI/CD pipelines
└── README.md
```

## Core Features

### 1. Product Management
- Create, read, update, delete products
- Product categorization
- Price management (purchase & selling)
- Stock level thresholds
- Bulk import/export

### 2. Inventory Management
- Real-time stock tracking
- Low stock alerts
- Inventory history
- Warehouse management
- Stock valuation

### 3. Inbound Orders (Purchases)
- Create purchase orders from suppliers
- Track order status (Draft → Pending → Received)
- Receive goods and update inventory
- Supplier management
- Order history and tracking

### 4. Outbound Orders (Sales)
- Create sales orders for customers
- Confirm and ship orders
- Profit calculation
- Customer management
- Delivery tracking

### 5. Reporting & Analytics
- Sales statistics
- Purchase analysis
- Profit/loss reports
- Inventory valuation
- Customer performance
- Supplier performance
- Exportable reports (Excel, PDF)

### 6. User Management
- Role-based access control (Admin, Warehouse, Sales, User)
- User authentication & authorization
- Department management
- Last login tracking
- User permissions

### 7. Audit & Logging
- Operation audit trail
- Change tracking
- User activity logs
- System event logging
- IP address and user agent tracking

### 8. Notifications & Alerts
- Low stock warnings
- Overdue order notifications
- System notifications
- Email alerts (future)

## API Endpoints

### Authentication
- `POST /api/auth/login` - User login
- `POST /api/auth/register` - User registration
- `GET /api/auth/me` - Get current user
- `POST /api/auth/logout` - User logout

### Products
- `GET /api/products` - List all products
- `GET /api/products/:id` - Get product details
- `POST /api/products` - Create product (Admin)
- `PUT /api/products/:id` - Update product (Admin)
- `DELETE /api/products/:id` - Delete product (Admin)
- `GET /api/products/low-stock` - Get low stock products

### Inventory
- `GET /api/inventory` - List inventory
- `GET /api/inventory/product/:productId` - Get product inventory
- `GET /api/inventory/low-stock` - Get low stock items
- `GET /api/inventory/summary` - Get inventory summary

### Inbound Orders
- `GET /api/inbound-orders` - List inbound orders
- `GET /api/inbound-orders/:id` - Get order details
- `POST /api/inbound-orders` - Create inbound order
- `PATCH /api/inbound-orders/:id/status` - Update order status

### Outbound Orders
- `GET /api/outbound-orders` - List outbound orders
- `GET /api/outbound-orders/:id` - Get order details
- `POST /api/outbound-orders` - Create outbound order
- `PATCH /api/outbound-orders/:id/confirm` - Confirm order
- `PATCH /api/outbound-orders/:id/status` - Update order status

## Installation & Setup

### Prerequisites
- Node.js (v16+)
- PostgreSQL (v12+)
- Docker & Docker Compose (optional)

### Backend Setup

```bash
cd backend
npm install
cp .env.example .env
npm run typeorm migration:run
npm run dev
```

### Frontend Setup

```bash
cd frontend
npm install
npm start
```

### Docker Setup

```bash
docker-compose up -d
```

## Environment Variables

### Backend (.env)
```
NODE_ENV=development
PORT=3000
DATABASE_URL=postgresql://user:password@localhost:5432/inventory_db
JWT_SECRET=your-secret-key
CORS_ORIGIN=http://localhost:3000
```

### Frontend (.env)
```
REACT_APP_API_URL=http://localhost:3000/api
```

## Database Schema

### Core Entities
- **User** - System users
- **Product** - Product catalog
- **Category** - Product categories
- **Inventory** - Stock levels
- **InboundOrder** - Purchase orders
- **InboundOrderItem** - Purchase order items
- **OutboundOrder** - Sales orders
- **OutboundOrderItem** - Sales order items
- **Supplier** - Supplier information
- **Customer** - Customer information
- **OperationLog** - Audit logs

## User Roles & Permissions

| Role | Permissions |
|------|-------------|
| **Admin** | Full system access, user management, system configuration |
| **Warehouse** | Create/manage inbound orders, inventory operations |
| **Sales** | Create/manage outbound orders, customer management |
| **User** | View-only access to reports and inventory data |

## Running Tests

```bash
# Backend tests
cd backend
npm run test

# Frontend tests
cd frontend
npm run test
```

## Building for Production

```bash
# Backend
cd backend
npm run build

# Frontend
cd frontend
npm run build
```

## Deployment

### Docker
```bash
docker-compose -f docker-compose.prod.yml up -d
```

### Manual Deployment
1. Build backend and frontend
2. Configure environment variables
3. Run database migrations
4. Start services with process manager (PM2, systemd, etc.)

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support, email support@example.com or create an issue in the GitHub repository.

## Roadmap

- [ ] Mobile application
- [ ] Advanced forecasting
- [ ] Integration with accounting software
- [ ] Multi-warehouse support
- [ ] Real-time collaboration features
- [ ] Machine learning recommendations
- [ ] API documentation (Swagger)
- [ ] Performance optimization
