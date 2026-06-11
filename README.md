# 🅿️ Park-Mitra - Intelligent Parking Management System

<div align="center">

![Node.js](https://img.shields.io/badge/Node.js-v14.0+-green?logo=node.js)
![React](https://img.shields.io/badge/React-v18.2+-blue?logo=react)
![SQLite](https://img.shields.io/badge/SQLite-3-blue?logo=sqlite)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Active%20Development-brightgreen)

**A comprehensive parking management solution for organizations with real-time slot booking, payment processing, and intelligent monitoring.**

[Features](#-features) • [Tech Stack](#-tech-stack) • [Installation](#-installation-guide) • [API Docs](#-api-documentation) • [Database](#-database-design)

</div>

---

## 📋 Project Overview

**Park-Mitra** is an enterprise-grade parking management system designed to solve the parking crisis in modern cities and organizations. The system enables users to book parking slots in advance, manage payments, track vehicle entry/exit, detect overstays, and collect penalties efficiently.

### Problem Statement
Parking management in organizations and public spaces is often chaotic, leading to:
- ❌ Inefficient space utilization
- ❌ Long vehicle queues and entry delays
- ❌ Difficulty tracking vehicle movements
- ❌ No systematic approach to penalty collection
- ❌ Manual record-keeping prone to errors

### Solution
Park-Mitra provides an automated, digital-first parking ecosystem that:
- ✅ Enables advance booking and real-time slot availability
- ✅ Automated payment processing and penalty collection
- ✅ QR code-based vehicle tracking
- ✅ Admin dashboards for comprehensive analytics
- ✅ Support for multiple parking organizations

---

## ✨ Features

### Core Parking Features
- **🎟️ Advanced Booking System**
  - Real-time slot availability checking
  - Advance booking with flexible duration
  - Support for organization members, visitors, and walk-in users
  - Automatic slot allocation from parking lots
  - QR code generation for each booking

- **💳 Payment Processing**
  - Multiple payment methods (UPI, Net Banking, Credit/Debit Card, Cash)
  - Online payment simulation for development
  - Real-time payment status tracking
  - Automated receipt generation
  - Payment history and transaction records

- **📍 Multi-Level Parking Support**
  - Multiple parking lots per organization
  - Priority-based slot allocation
  - Individual lot management and configuration
  - Detailed lot statistics and utilization tracking

- **🚗 Vehicle Tracking**
  - QR code-based entry/exit verification
  - Real-time vehicle location tracking
  - Automated entry and exit time recording
  - Vehicle history for each user

### Admin & Organization Features
- **👨‍💼 Organization Management Dashboard**
  - Create and manage parking organizations
  - Configure pricing and occupancy rules
  - View real-time parking statistics
  - Manage organization members and employees
  - Revenue and payment analytics

- **👮 Watchman Portal**
  - Monitor parking entry/exit
  - Verify vehicle details via QR codes
  - Manually mark vehicle entry/exit if QR fails
  - Report incidents and issues
  - Access booking and payment information

- **📊 Advanced Analytics**
  - Occupancy rate tracking
  - Peak hour analysis
  - Revenue reports
  - User demographic insights
  - Slot utilization statistics

### Smart Penalty System
- **⚠️ Overstay Detection**
  - Automatic overstay calculation
  - Configurable penalty rates
  - Progressive penalty calculation
  - Penalty payment tracking

- **🅿️ Informal Parking Support**
  - Street parking simulation
  - Location-based informal parking spots
  - Hourly rate management
  - Availability tracking for informal locations

### User Experience Features
- **👤 User Profile Management**
  - Multi-role support (Member, Visitor, Walk-in, Watchman, Admin)
  - Booking history and status tracking
  - Payment history
  - Profile customization
  - Password management

- **🔔 Notifications & Updates**
  - Real-time booking confirmations
  - Payment status updates
  - Overstay alerts
  - Penalty notifications

- **🔐 Security Features**
  - JWT-based authentication
  - Bcrypt password hashing
  - Role-based access control (RBAC)
  - Rate limiting on API endpoints
  - Security headers implementation

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| **React 18.2** | UI framework for dynamic user interfaces |
| **React Router v6** | Client-side routing |
| **Tailwind CSS** | Utility-first CSS framework for styling |
| **Axios** | HTTP client for API communication |
| **QRCode.React** | QR code generation for frontend display |
| **HTML5 QRCode** | QR code scanning and detection |
| **React Toastify** | Toast notifications for user feedback |
| **React Icons** | Icon library (4.11.0) |
| **Date-fns** | Date manipulation and formatting |

### Backend
| Technology | Purpose |
|-----------|---------|
| **Node.js** | Runtime environment |
| **Express.js 4.18** | Web framework and routing |
| **SQLite3** | Lightweight relational database |
| **JWT (jsonwebtoken 9.0)** | Secure token-based authentication |
| **Bcrypt 5.1** | Password hashing and encryption |
| **Helmet** | Security middleware for HTTP headers |
| **CORS** | Cross-Origin Resource Sharing |
| **Morgan** | HTTP request logging |
| **Express Rate Limit** | API rate limiting for DDoS protection |
| **QRCode (Node)** | Backend QR code generation |
| **Dotenv** | Environment variable management |
| **Body Parser** | Middleware for parsing request bodies |

### Database
| Component | Details |
|-----------|---------|
| **Type** | SQLite3 |
| **Location** | `/parkmitra.db` |
| **Features** | ACID compliance, Foreign key constraints, Indexes for optimization |
| **Size** | Lightweight (suitable for small to medium deployments) |

### Development Tools
| Tool | Purpose |
|------|---------|
| **Nodemon** | Automatic server restart during development |
| **Jest** | Unit testing framework |
| **Supertest** | HTTP testing library |
| **ESLint** | Code linting |
| **Prettier** | Code formatting |

### Cloud & Hosting
- **Current**: Local development environment
- **Recommended**: AWS EC2, Heroku, or DigitalOcean for production
- **Database**: Can be migrated to PostgreSQL for production scalability

---

## 🏗️ Project Architecture

### High-Level Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER CLIENTS                              │
│  ┌──────────────────┐  ┌──────────────────┐  ┌──────────────┐  │
│  │  Mobile Browser  │  │  Desktop Browser │  │  Watchman   │  │
│  │   (Visitors)     │  │  (Organization)  │  │   Portal    │  │
│  └──────────────────┘  └──────────────────┘  └──────────────┘  │
└────────────────────┬────────────────────────────────────────────┘
                     │ HTTPS/REST API
                     ▼
┌─────────────────────────────────────────────────────────────────┐
│                   REACT FRONTEND (3000)                          │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │  Auth          │ Booking     │ Payment  │ Dashboard      │  │
│  │  Components    │ Components  │ Module   │ Components     │  │
│  └──────────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │  Context: AuthContext, BookingContext                   │  │
│  │  Utils: API client, Validators, QR Generator            │  │
│  └──────────────────────────────────────────────────────────┘  │
└────────────────────┬────────────────────────────────────────────┘
                     │ HTTP/JSON
                     ▼
┌─────────────────────────────────────────────────────────────────┐
│               EXPRESS.JS BACKEND (5000)                          │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │ Middleware Layer                                         │  │
│  │ ├─ CORS, Body Parser, Rate Limiter                     │  │
│  │ ├─ Security Headers, Request Logger                    │  │
│  │ └─ Error Handler                                        │  │
│  └──────────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │ Routes Layer                                             │  │
│  │ ├─ /api/auth (authentication)                           │  │
│  │ ├─ /api/bookings (parking bookings)                     │  │
│  │ ├─ /api/payments (payment processing)                  │  │
│  │ ├─ /api/organizations (org management)                 │  │
│  │ ├─ /api/watchmen (watchman operations)                 │  │
│  │ ├─ /api/parking-lots (lot management)                  │  │
│  │ └─ /api/informal-parking (street parking)              │  │
│  └──────────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │ Controllers & Models Layer                              │  │
│  │ ├─ Auth Controller     ├─ User Model                   │  │
│  │ ├─ Booking Controller  ├─ Booking Model                │  │
│  │ ├─ Payment Controller  ├─ Payment Model                │  │
│  │ ├─ Org Controller      ├─ Organization Model           │  │
│  │ └─ Watchman Controller └─ Parking Lot Model            │  │
│  └──────────────────────────────────────────────────────────┘  │
└────────────────────┬────────────────────────────────────────────┘
                     │ SQL Queries
                     ▼
┌─────────────────────────────────────────────────────────────────┐
│                    SQLite DATABASE                               │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │ Core Tables:                                             │  │
│  │ ├─ users              (users, members, visitors)        │  │
│  │ ├─ organizations      (org details, pricing)            │  │
│  │ ├─ parking_lots       (lot configuration)               │  │
│  │ ├─ bookings           (reservations, status)            │  │
│  │ ├─ payments           (transactions, receipts)          │  │
│  │ ├─ watchmen           (staff management)                │  │
│  │ └─ informal_parking   (street spot simulation)          │  │
│  └──────────────────────────────────────────────────────────┘  │
│  Indexes: Email, Mobile, Booking Status, Organization ID       │
└─────────────────────────────────────────────────────────────────┘
```

### Data Flow

1. **User Registration/Login**
   - User submits credentials → Express receives request → Bcrypt verification → JWT token generated → Token stored in frontend localStorage

2. **Booking Flow**
   - User searches availability → Backend checks parking_lots availability → Slot allocation → QR code generation → Booking confirmation

3. **Payment Flow**
   - User initiates payment → Payment simulation (95% success rate) → Database transaction update → Receipt generation → Payment confirmation

4. **Entry/Exit Tracking**
   - Vehicle scans QR code → Watchman verifies via portal → Entry time recorded → Exit time recorded on departure → Overstay calculation

### Component Interaction

```
Frontend                    API               Backend              Database
┌─────────────────┐
│ Login Component │─────GET /api/auth/login────→
│                 │                          ┌─────────────────┐
│                 │◄─────JWT Token──────────┤ Auth Controller │
└─────────────────┘                         └─────────────────┘

┌─────────────────┐
│ Booking Form    │─────POST /api/bookings/create────→
│                 │                          ┌──────────────────┐
│                 │◄──Booking ID + QR Code──│ Booking Controller│
└─────────────────┘                         └──────────────────┘
                                                     │
                                                     ▼
                                            ┌─────────────────┐
                                            │  SQLite Database│
                                            └─────────────────┘
```

---

## 📁 Folder Structure

```
Park-Mitra-Final/
├── 📄 package.json                    # Root dependencies and scripts
├── 📄 server.js                       # Express server entry point
├── 📄 .env.example                    # Environment variables template
├── 📄 .gitignore                      # Git ignore rules
├── 📄 README.md                       # This file
│
├── 🗂️ backend/                        # Node.js/Express Backend
│   ├── 📄 config/
│   │   ├── auth.config.js             # JWT & password configuration
│   │   └── db.js                      # SQLite connection & initialization
│   │
│   ├── 📄 database/
│   │   ├── schema.sql                 # Complete database schema
│   │   ├── seed.sql                   # Sample data
│   │   ├── init-db.js                 # Database initialization script
│   │   ├── seed-db.js                 # Database seeding
│   │   ├── migrations/                # Database migration files
│   │   │   ├── 001_add_parking_lots_table.sql
│   │   │   ├── add_confirmed_booking_status.sql
│   │   │   ├── add_overstay_columns.sql
│   │   │   ├── add_payment_type_column.sql
│   │   │   ├── fix_duplicate_slot_bookings.sql
│   │   │   └── ... (more migrations)
│   │   └── ... (utility scripts)
│   │
│   ├── 📄 controllers/
│   │   ├── authController.js          # Authentication logic
│   │   ├── bookingController.js       # Booking operations
│   │   ├── paymentController.js       # Payment processing
│   │   ├── organizationController.js  # Org management
│   │   └── watchmanController.js      # Watchman operations
│   │
│   ├── 📄 models/
│   │   ├── User.js                    # User model & queries
│   │   ├── Organization.js            # Organization model
│   │   ├── Booking.js                 # Booking model
│   │   ├── Payment.js                 # Payment model
│   │   ├── ParkingLot.js              # Parking lot model
│   │   └── Watchman.js                # Watchman model
│   │
│   ├── 📄 routes/
│   │   ├── auth.js                    # Auth endpoints
│   │   ├── bookings.js                # Booking endpoints
│   │   ├── payments.js                # Payment endpoints
│   │   ├── organizations.js           # Organization endpoints
│   │   ├── watchmen.js                # Watchman endpoints
│   │   ├── parking-lots.js            # Parking lot endpoints
│   │   └── informal-parking.js        # Street parking endpoints
│   │
│   ├── 📄 middleware/
│   │   ├── auth.js                    # JWT verification middleware
│   │   ├── validation.js              # Input validation middleware
│   │   ├── errorHandler.js            # Global error handler
│   │   ├── logger.js                  # Request logging
│   │   ├── rateLimiter.js             # Rate limiting
│   │   └── securityHeaders.js         # Security headers
│   │
│   └── 📄 utils/
│       ├── qrGenerator.js             # QR code generation
│       ├── responseHelper.js          # Standard response formatting
│       ├── validators.js              # Validation utilities
│       ├── dateHelper.js              # Date/time utilities
│       └── organizationDeletion.js    # Org cleanup utilities
│
├── 🗂️ frontend/                       # React Frontend
│   ├── 📄 package.json                # Frontend dependencies
│   ├── 📄 postcss.config.js           # PostCSS configuration
│   ├── 📄 tailwind.config.js          # Tailwind CSS configuration
│   │
│   └── 📄 src/
│       ├── 📄 index.js                # React entry point
│       ├── 📄 App.js                  # Main App component with routing
│       ├── 📄 App.css                 # Global styles
│       │
│       ├── 🗂️ components/             # Reusable components
│       │   ├── Auth/                  # Login, Register, OAuth
│       │   ├── Booking/               # Booking form, list, history
│       │   ├── Dashboard/             # User dashboard
│       │   ├── Admin/                 # Organization admin panel
│       │   ├── Watchman/              # Watchman portal
│       │   ├── Payment/               # Payment processing
│       │   ├── QRCode/                # QR code display & scan
│       │   ├── InformalParking/       # Street parking finder
│       │   ├── Profile/               # User profile management
│       │   ├── Landing/               # Home page
│       │   └── Common/                # Shared: Navbar, Footer, etc.
│       │
│       ├── 🗂️ context/                # State management
│       │   ├── AuthContext.js         # Authentication state
│       │   └── BookingContext.js      # Booking state
│       │
│       ├── 🗂️ services/               # API communication
│       │   ├── api.js                 # Axios instance & interceptors
│       │   ├── authService.js         # Auth API calls
│       │   ├── bookingService.js      # Booking API calls
│       │   ├── paymentService.js      # Payment API calls
│       │   └── ... (more services)
│       │
│       ├── 🗂️ utils/                  # Utility functions
│       │   ├── validators.js          # Client-side validation
│       │   ├── dateFormatter.js       # Date formatting
│       │   └── constants.js           # App constants
│       │
│       ├── 🗂️ styles/                 # CSS modules
│       │   └── *.module.css           # Component-specific styles
│       │
│       ├── 🗂️ assets/                 # Static resources
│       │   ├── images/                # Project images
│       │   └── icons/                 # Icon assets
│       │
│       └── index.css                  # Global styles
│
└── 🗂️ node_modules/                  # Dependencies (auto-generated)
```

---

## 🚀 Installation Guide

### Prerequisites

- **Node.js**: v14.0 or higher ([Download](https://nodejs.org/))
- **npm**: v6.0 or higher (comes with Node.js)
- **Git**: For cloning the repository ([Download](https://git-scm.com/))
- **SQLite3**: Should be included with Node.js
- **Code Editor**: VS Code recommended ([Download](https://code.visualstudio.com/))

### Step-by-Step Setup

#### 1️⃣ Clone the Repository

```bash
# Clone the repository
git clone https://github.com/Shravani-kurkute/Park-Mitra-Final.git

# Navigate to project directory
cd Park-Mitra-Final
```

#### 2️⃣ Install Root Dependencies

```bash
# Install root level dependencies
npm install
```

#### 3️⃣ Set Up Environment Variables

```bash
# Copy the example env file
cp .env.example .env

# Edit .env with your configuration
# Windows
notepad .env

# macOS/Linux
nano .env
```

**Configure these variables in `.env`:**

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# JWT Authentication
JWT_SECRET=your_secure_random_string_change_in_production

# Database
DATABASE_PATH=./parkmitra.db

# Frontend URL (for CORS)
FRONTEND_URL=http://localhost:3000

# Optional (for future features)
# EMAIL_SERVICE=smtp
# SMS_API_KEY=your_api_key
# PAYMENT_GATEWAY_KEY=your_key
```

#### 4️⃣ Initialize Database

```bash
# Create database tables and structure
npm run init-db

# Seed database with sample data (optional)
npm run seed-db

# Verify database setup
npm run test-db
```

#### 5️⃣ Install Backend Dependencies

```bash
# Dependencies are already installed from step 2
# But you can verify by checking package.json
cat package.json
```

#### 6️⃣ Install Frontend Dependencies

```bash
# Navigate to frontend directory
cd frontend

# Install React dependencies
npm install

# Return to root
cd ..
```

#### 7️⃣ Configure Frontend API URL (Optional)

```bash
# Create .env in frontend directory
cd frontend
echo "REACT_APP_API_BASE_URL=http://localhost:5000/api" > .env
cd ..
```

#### 8️⃣ Running the Application

**Option A: Run Both Servers (Development)**

```bash
# Open terminal and run backend
npm start

# In another terminal, run frontend
npm run client
```

The application will be available at:
- 🖥️ Frontend: http://localhost:3000
- 🔌 Backend API: http://localhost:5000

**Option B: Run Backend Only**

```bash
npm start
```

**Option C: Run Frontend Only**

```bash
npm run client
```

**Option D: Development Mode with Auto-Reload**

```bash
# Backend with nodemon (auto-restart on changes)
npm run dev

# Frontend with React dev server (already has hot reload)
npm run client
```

#### 9️⃣ Build for Production

```bash
# Build the React frontend
npm run build

# Output: frontend/build/ directory ready for deployment
```

#### 🔟 Verify Installation

```bash
# Check backend health
curl http://localhost:5000/api/health

# Expected response:
# {
#   "status": "success",
#   "message": "Server is running",
#   "environment": "development"
# }
```

### Troubleshooting Installation

| Issue | Solution |
|-------|----------|
| `npm install` fails | Clear npm cache: `npm cache clean --force` then retry |
| Database already exists | Delete `parkmitra.db` and re-run `npm run init-db` |
| Port 5000 in use | Change PORT in .env or kill process: `lsof -i :5000` |
| CORS errors | Verify FRONTEND_URL in .env matches frontend URL |
| JWT errors | Regenerate JWT_SECRET: Generate random string and update .env |
| Module not found | Delete `node_modules` and `package-lock.json`, then `npm install` |

---

## 🔧 Environment Variables

### Backend Environment Variables

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `PORT` | Number | 5000 | Server port for backend API |
| `NODE_ENV` | String | development | Environment (development/production) |
| `JWT_SECRET` | String | parkmitra_secret_key | Secret key for JWT token generation |
| `JWT_EXPIRES_IN` | String | 24h | JWT token expiration time |
| `DATABASE_PATH` | String | ./parkmitra.db | Path to SQLite database file |
| `FRONTEND_URL` | String | http://localhost:3000 | Frontend URL for CORS configuration |
| `DB_PATH` | String | ./parkmitra.db | Alternative database path variable |

### Frontend Environment Variables

| Variable | Type | Default | Description |
|----------|------|---------|-------------|
| `REACT_APP_API_BASE_URL` | String | http://localhost:5000/api | Backend API base URL |
| `REACT_APP_ENV` | String | development | Frontend environment |

### Security Recommendations

⚠️ **Production Configuration:**

```env
# 1. Change JWT_SECRET to a secure random string (64+ characters)
JWT_SECRET=your_very_long_and_secure_random_string_here_minimum_64_characters

# 2. Set NODE_ENV to production
NODE_ENV=production

# 3. Update FRONTEND_URL to your domain
FRONTEND_URL=https://yourdomain.com

# 4. Use environment-specific database
DATABASE_PATH=/var/lib/park-mitra/database.db

# 5. Consider using PostgreSQL for production
# DATABASE_URL=postgresql://user:password@host:port/database
```

---

## 📖 Usage Guide

### For End Users (Visitors/Organization Members)

#### Creating an Account

1. Navigate to **Register** page
2. Choose user type:
   - **Visitor**: One-time or occasional parking
   - **Organization Member**: Employee of a registered organization
   - **Walk-in**: Access without advance registration
3. Fill in details:
   - Name, Email, Mobile (10 digits)
   - Password (min 8 chars, 1 uppercase, 1 lowercase, 1 number)
4. Click "Register"
5. Login with credentials

#### Booking a Parking Slot

1. Login to user dashboard
2. Click **"Book Parking"**
3. Select organization/parking location
4. Choose date and time
5. Select duration
6. Review pricing
7. Confirm booking
8. **Receive QR Code** for vehicle identification
9. Save or print QR code

#### Making Payment

1. Go to **"My Bookings"**
2. Select booking with pending payment
3. Choose payment method:
   - UPI
   - Net Banking
   - Credit/Debit Card
   - Cash (at entry)
4. Verify amount and click "Pay"
5. Complete payment authentication
6. Receive payment confirmation

#### Entry/Exit at Parking

1. **At Entry**:
   - Display QR code to watchman
   - Watchman scans code or verifies manually
   - Vehicle allowed to enter

2. **At Exit**:
   - QR code scanned
   - Exit time recorded automatically
   - System checks for overstay
   - If overstay, penalty calculated and notified

### For Organization Admins

#### Setting Up Organization

1. Go to **Admin Registration**
2. Fill organization details:
   - Organization name
   - Admin name and email
   - Address and contact
   - Total parking slots
   - Pricing (member free or visitor hourly rate)
3. Create admin account
4. Receive organization ID

#### Managing Parking Lots

1. Login to **Admin Dashboard**
2. Go to **"Parking Lots"**
3. Create new lot:
   - Lot name and description
   - Total slots
   - Priority order
4. Edit lot settings:
   - Change availability
   - Activate/deactivate lot
   - Update slot count

#### Monitoring Dashboard

1. View **Real-time Statistics**:
   - Current occupancy
   - Available slots
   - Revenue today
   - Total bookings

2. View **Detailed Reports**:
   - Occupancy by time
   - Revenue by payment method
   - Top parking slots
   - Peak hours

#### Managing Staff (Watchmen)

1. Go to **"Staff Management"**
2. Add new watchman:
   - Employee ID
   - Name, email, mobile
   - Shift hours
3. Edit watchman details
4. Monitor watchman activity logs

### For Watchmen

#### Portal Login

1. Use employee ID and password
2. Access **Watchman Dashboard**

#### Verifying Vehicles

1. **For Entry**:
   - Request QR code from driver
   - Scan QR code using phone/tablet
   - Verify booking details
   - Mark entry (auto-marked on scan)

2. **For Exit**:
   - Scan QR code again
   - Check for overstay penalty
   - If penalty due, collect cash
   - Record exit time

#### Cash Payment Collection

1. If payment due at exit
2. Select payment method: **Cash**
3. Enter amount collected
4. System records cash transaction
5. Provide receipt to driver

---

## 🔌 API Documentation

### Base URL
```
http://localhost:5000/api
```

### Authentication
All protected endpoints require JWT token in header:
```
Authorization: Bearer <your_jwt_token>
```

### Response Format
```json
{
  "success": true,
  "message": "Operation successful",
  "data": { /* response data */ },
  "error": null
}
```

---

### Authentication Endpoints

#### Register User

**POST** `/auth/register`

```bash
curl -X POST http://localhost:5000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "email": "john@example.com",
    "mobile": "9876543210",
    "password": "SecurePass123",
    "user_type": "visitor"
  }'
```

**Request Body:**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "mobile": "9876543210",
  "password": "SecurePass123",
  "user_type": "visitor|organization_member|walk_in",
  "organization_id": 1,          // Optional, required if organization_member
  "employee_id": "EMP001"        // Optional, required if organization_member
}
```

**Response:**
```json
{
  "success": true,
  "message": "User registered successfully",
  "data": {
    "user_id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "user_type": "visitor"
  }
}
```

---

#### Login

**POST** `/auth/login`

```bash
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{
    "email": "john@example.com",
    "password": "SecurePass123"
  }'
```

**Request Body:**
```json
{
  "email": "john@example.com",
  "password": "SecurePass123"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Login successful",
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "user": {
      "user_id": 1,
      "name": "John Doe",
      "email": "john@example.com",
      "user_type": "visitor"
    },
    "expiresIn": "24h"
  }
}
```

---

### Booking Endpoints

#### Create Booking

**POST** `/bookings/create`

Requires: Authentication token

```bash
curl -X POST http://localhost:5000/api/bookings/create \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{
    "organization_id": 1,
    "vehicle_number": "DL01AB1234",
    "booking_start_time": "2024-06-15T10:00:00",
    "booking_end_time": "2024-06-15T14:00:00"
  }'
```

**Request Body:**
```json
{
  "organization_id": 1,
  "vehicle_number": "DL01AB1234",
  "booking_start_time": "2024-06-15T10:00:00",
  "booking_end_time": "2024-06-15T14:00:00"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Booking created successfully",
  "data": {
    "booking_id": 123,
    "qr_code_data": "PARKMITRA_123_ABC",
    "amount": 200,
    "booking_status": "confirmed",
    "payment_status": "pending"
  }
}
```

---

#### Get User Bookings

**GET** `/bookings/user`

Requires: Authentication token

```bash
curl -X GET http://localhost:5000/api/bookings/user \
  -H "Authorization: Bearer <token>"
```

**Response:**
```json
{
  "success": true,
  "message": "Bookings retrieved successfully",
  "data": [
    {
      "id": 123,
      "vehicle_number": "DL01AB1234",
      "booking_status": "confirmed",
      "payment_status": "pending",
      "amount": 200,
      "booking_start_time": "2024-06-15T10:00:00",
      "booking_end_time": "2024-06-15T14:00:00"
    }
  ]
}
```

---

#### Mark Entry

**PUT** `/bookings/:booking_id/mark-entry`

Requires: Authentication token (Watchman)

```bash
curl -X PUT http://localhost:5000/api/bookings/123/mark-entry \
  -H "Authorization: Bearer <watchman_token>"
```

**Response:**
```json
{
  "success": true,
  "message": "Entry marked successfully",
  "data": {
    "booking_id": 123,
    "entry_time": "2024-06-15T10:05:00",
    "booking_status": "active"
  }
}
```

---

#### Mark Exit

**PUT** `/bookings/:booking_id/mark-exit`

Requires: Authentication token (Watchman)

```bash
curl -X PUT http://localhost:5000/api/bookings/123/mark-exit \
  -H "Authorization: Bearer <watchman_token>"
```

**Response:**
```json
{
  "success": true,
  "message": "Exit marked successfully",
  "data": {
    "booking_id": 123,
    "exit_time": "2024-06-15T14:10:00",
    "booking_status": "completed",
    "overstay_minutes": 10,
    "penalty_amount": 50
  }
}
```

---

### Payment Endpoints

#### Simulate Online Payment

**POST** `/payments/simulate-online`

Requires: Authentication token

```bash
curl -X POST http://localhost:5000/api/payments/simulate-online \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{
    "booking_id": 123,
    "amount": 200,
    "payment_method_type": "upi"
  }'
```

**Request Body:**
```json
{
  "booking_id": 123,
  "amount": 200,
  "payment_method_type": "upi|card|netbanking"
}
```

**Response:**
```json
{
  "success": true,
  "message": "Payment processed successfully",
  "data": {
    "transaction_id": "TXN_123456_ABC",
    "booking_id": 123,
    "amount": 200,
    "payment_status": "completed",
    "payment_method": "UPI",
    "timestamp": "2024-06-15T10:00:00"
  }
}
```

---

#### Get Payment History

**GET** `/payments/history`

Requires: Authentication token

```bash
curl -X GET http://localhost:5000/api/payments/history \
  -H "Authorization: Bearer <token>"
```

**Response:**
```json
{
  "success": true,
  "message": "Payment history retrieved",
  "data": [
    {
      "id": 1,
      "booking_id": 123,
      "amount": 200,
      "payment_method": "UPI",
      "payment_status": "completed",
      "transaction_id": "TXN_123456_ABC",
      "created_at": "2024-06-15T10:00:00"
    }
  ]
}
```

---

### Organization Endpoints

#### Register Organization

**POST** `/organizations/register`

```bash
curl -X POST http://localhost:5000/api/organizations/register \
  -H "Content-Type: application/json" \
  -d '{
    "org_name": "VIIT Parking",
    "admin_name": "Admin User",
    "admin_email": "admin@viit.edu",
    "admin_mobile": "9876543210",
    "address": "VIIT Campus, Pune",
    "total_slots": 500,
    "visitor_hourly_rate": 30,
    "member_parking_free": true
  }'
```

**Response:**
```json
{
  "success": true,
  "message": "Organization registered successfully",
  "data": {
    "organization_id": 1,
    "org_name": "VIIT Parking",
    "admin_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
}
```

---

#### Get Organization Dashboard

**GET** `/organizations/dashboard/:orgId`

Requires: Authentication token (Organization Admin)

```bash
curl -X GET http://localhost:5000/api/organizations/dashboard/1 \
  -H "Authorization: Bearer <admin_token>"
```

**Response:**
```json
{
  "success": true,
  "message": "Dashboard data retrieved",
  "data": {
    "occupancy_rate": "75%",
    "available_slots": 125,
    "total_bookings_today": 45,
    "revenue_today": 2250,
    "active_vehicles": 75,
    "top_parking_lots": [...]
  }
}
```

---

### Parking Lot Endpoints

#### Get Available Lots

**GET** `/parking-lots/:orgId/available`

```bash
curl -X GET http://localhost:5000/api/parking-lots/1/available
```

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "lot_id": 1,
      "lot_name": "Ground Floor",
      "total_slots": 100,
      "available_slots": 35,
      "hourly_rate": 30
    },
    {
      "lot_id": 2,
      "lot_name": "First Floor",
      "total_slots": 150,
      "available_slots": 45,
      "hourly_rate": 30
    }
  ]
}
```

---

### Error Responses

**400 Bad Request**
```json
{
  "success": false,
  "message": "Invalid input parameters",
  "error": "organization_id, vehicle_number, and booking times are required"
}
```

**401 Unauthorized**
```json
{
  "success": false,
  "message": "Authentication required",
  "error": "Invalid or expired token"
}
```

**403 Forbidden**
```json
{
  "success": false,
  "message": "Access denied",
  "error": "You do not have permission to access this resource"
}
```

**404 Not Found**
```json
{
  "success": false,
  "message": "Resource not found",
  "error": "Booking with ID 999 not found"
}
```

**500 Internal Server Error**
```json
{
  "success": false,
  "message": "An error occurred",
  "error": "Database connection error"
}
```

---

## 🗄️ Database Design

### Database Schema Overview

The Park-Mitra system uses SQLite with 7 main tables and optimized indexing.

### Core Tables

#### 1. Organizations Table
```sql
CREATE TABLE organizations (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  org_name VARCHAR(255) NOT NULL,
  admin_name VARCHAR(255) NOT NULL,
  admin_email VARCHAR(255) UNIQUE NOT NULL,
  admin_mobile VARCHAR(10) NOT NULL,
  address TEXT NOT NULL,
  total_slots INTEGER NOT NULL,
  available_slots INTEGER NOT NULL,
  member_parking_free BOOLEAN DEFAULT 1,
  visitor_hourly_rate DECIMAL(10, 2),
  parking_rules TEXT,
  operating_hours TEXT,
  created_at DATETIME,
  updated_at DATETIME
);
```

**Purpose**: Stores organization/parking provider information
**Key Fields**: 
- `org_name`: Organization identifier
- `total_slots`: Capacity management
- `visitor_hourly_rate`: Dynamic pricing

---

#### 2. Parking Lots Table
```sql
CREATE TABLE parking_lots (
  lot_id INTEGER PRIMARY KEY AUTOINCREMENT,
  organization_id INTEGER NOT NULL,
  lot_name VARCHAR(255) NOT NULL,
  lot_description TEXT,
  total_slots INTEGER NOT NULL,
  available_slots INTEGER NOT NULL,
  priority_order INTEGER DEFAULT 1,
  is_active BOOLEAN DEFAULT 1,
  created_at DATETIME,
  updated_at DATETIME,
  FOREIGN KEY (organization_id) REFERENCES organizations(id)
);
```

**Purpose**: Manage multiple parking lots within an organization
**Key Fields**:
- `priority_order`: Slot allocation sequence
- `is_active`: Enable/disable lot

---

#### 3. Users Table
```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  mobile VARCHAR(10) NOT NULL,
  password VARCHAR(255) NOT NULL,
  user_type VARCHAR(50) NOT NULL CHECK(user_type IN ('organization_member', 'visitor', 'walk_in')),
  organization_id INTEGER,
  employee_id VARCHAR(100),
  is_verified BOOLEAN DEFAULT 0,
  created_at DATETIME,
  updated_at DATETIME,
  FOREIGN KEY (organization_id) REFERENCES organizations(id)
);
```

**Purpose**: Store all user information
**User Types**:
- `organization_member`: Employee with member benefits
- `visitor`: Regular parking customer
- `walk_in`: Unregistered user

---

#### 4. Bookings Table
```sql
CREATE TABLE bookings (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  user_id INTEGER NOT NULL,
  organization_id INTEGER NOT NULL,
  parking_lot_id INTEGER,
  vehicle_number VARCHAR(50) NOT NULL,
  slot_number VARCHAR(50),
  booking_start_time DATETIME NOT NULL,
  booking_end_time DATETIME NOT NULL,
  duration_hours DECIMAL(5, 2) NOT NULL,
  amount DECIMAL(10, 2) DEFAULT 0,
  payment_status VARCHAR(50) DEFAULT 'pending',
  booking_status VARCHAR(50) DEFAULT 'confirmed',
  qr_code_data TEXT,
  entry_time DATETIME,
  exit_time DATETIME,
  overstay_minutes INTEGER DEFAULT 0,
  penalty_amount DECIMAL(10, 2) DEFAULT 0,
  created_at DATETIME,
  updated_at DATETIME,
  FOREIGN KEY (user_id) REFERENCES users(id),
  FOREIGN KEY (organization_id) REFERENCES organizations(id),
  FOREIGN KEY (parking_lot_id) REFERENCES parking_lots(lot_id)
);
```

**Purpose**: Core booking/reservation management
**Statuses**:
- `confirmed`: Booking accepted
- `active`: Vehicle currently parked
- `completed`: Booking finished
- `cancelled`: Cancelled booking
- `overstay`: Vehicle exceeded duration

---

#### 5. Payments Table
```sql
CREATE TABLE payments (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  booking_id INTEGER NOT NULL,
  amount DECIMAL(10, 2) NOT NULL,
  payment_method VARCHAR(50) NOT NULL CHECK(payment_method IN ('UPI', 'Net Banking', 'Credit Card', 'Debit Card', 'Cash')),
  payment_type VARCHAR(50) DEFAULT 'booking' CHECK(payment_type IN ('booking', 'penalty')),
  payment_status VARCHAR(50) DEFAULT 'pending',
  transaction_id VARCHAR(255) UNIQUE,
  watchman_id INTEGER,
  payment_timestamp DATETIME DEFAULT CURRENT_TIMESTAMP,
  created_at DATETIME,
  FOREIGN KEY (booking_id) REFERENCES bookings(id),
  FOREIGN KEY (watchman_id) REFERENCES watchmen(id)
);
```

**Purpose**: Transaction tracking and revenue management
**Payment Types**:
- `booking`: Regular parking charges
- `penalty`: Overstay penalties

---

#### 6. Watchmen Table
```sql
CREATE TABLE watchmen (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  mobile VARCHAR(10) NOT NULL,
  employee_id VARCHAR(50) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  organization_id INTEGER NOT NULL,
  shift_start TIME,
  shift_end TIME,
  assigned_shift VARCHAR(50),
  is_active BOOLEAN DEFAULT 1,
  created_at DATETIME,
  updated_at DATETIME,
  FOREIGN KEY (organization_id) REFERENCES organizations(id)
);
```

**Purpose**: Parking staff management
**Key Fields**:
- `shift_start/shift_end`: Work hours
- `is_active`: Staff status

---

#### 7. Informal Parking Table
```sql
CREATE TABLE informal_parking (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  location_name VARCHAR(255) NOT NULL,
  address TEXT NOT NULL,
  latitude DECIMAL(10, 8),
  longitude DECIMAL(11, 8),
  total_spots INTEGER NOT NULL,
  available_spots INTEGER NOT NULL,
  hourly_rate DECIMAL(10, 2) NOT NULL,
  is_simulated BOOLEAN DEFAULT 1,
  created_at DATETIME
);
```

**Purpose**: Street/informal parking simulation
**Key Fields**:
- `latitude/longitude`: GPS coordinates
- `is_simulated`: Demo data flag

---

### Database Relationships

```
organizations (1) ─── (many) users
     │
     ├─ (1) ─── (many) parking_lots
     │
     ├─ (1) ─── (many) bookings
     │
     ├─ (1) ─── (many) watchmen
     │
     └─ (1) ─── (many) payments

parking_lots (1) ─── (many) bookings

users (1) ─── (many) bookings

bookings (1) ─── (many) payments

watchmen (1) ─── (many) payments
```

### Performance Optimization

**Indexes Created:**

| Index | Table | Columns | Purpose |
|-------|-------|---------|---------|
| idx_users_email | users | email | Fast email lookup for login |
| idx_users_mobile | users | mobile | Mobile verification |
| idx_users_organization_id | users | organization_id | Org member queries |
| idx_bookings_user_id | bookings | user_id | User booking history |
| idx_bookings_booking_status | bookings | booking_status | Status-based queries |
| idx_bookings_payment_status | bookings | payment_status | Payment tracking |
| idx_bookings_start_time | bookings | booking_start_time | Availability checking |
| idx_watchmen_organization_id | watchmen | organization_id | Watchman lookup |
| idx_payments_booking_id | payments | booking_id | Payment history |

### Query Examples

#### Find Available Slots
```sql
SELECT * FROM parking_lots 
WHERE organization_id = 1 AND is_active = 1
ORDER BY priority_order
```

#### Get User Booking History
```sql
SELECT * FROM bookings 
WHERE user_id = 5 
ORDER BY booking_start_time DESC
```

#### Calculate Revenue
```sql
SELECT 
  SUM(amount) as total_revenue,
  COUNT(*) as transaction_count,
  DATE(payment_timestamp) as date
FROM payments 
WHERE organization_id = 1 AND payment_status = 'completed'
GROUP BY DATE(payment_timestamp)
```

#### Detect Overstays
```sql
SELECT * FROM bookings 
WHERE booking_status = 'active' 
AND booking_end_time < CURRENT_TIMESTAMP
```

---

## 🎨 Screenshots & UI Mockups

### Landing Page
```
[Login Button]              [Features]              [Pricing]
                PARK-MITRA LOGO
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
            Smart Parking Management Solution
     Revolutionizing Urban Parking Experiences
                [Get Started Button]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Features    |  Real-time Availability  |  Smart Booking  |
            |  Easy Payment  |  QR Tracking  |  Admin Analytics
```

### User Dashboard
```
┌─────────────────────────────────────────────────────┐
│ Welcome, John!              [Profile] [Logout]      │
├─────────────────────────────────────────────────────┤
│ [Book Parking]  [My Bookings]  [Payments]  [Help]   │
├─────────────────────────────────────────────────────┤
│                                                     │
│  Active Bookings:                                  │
│  ┌─────────────────────────────────────────────┐   │
│  │ VIIT Parking - Ground Floor                │   │
│  │ Vehicle: DL01AB1234                        │   │
│  │ Time: 10:00 AM - 02:00 PM  Status: ACTIVE │   │
│  │                               [View Details]│   │
│  └─────────────────────────────────────────────┘   │
│                                                     │
│  Recent Transactions:                              │
│  ├─ Payment Completed: ₹200 (23 May)             │
│  ├─ Booking Cancelled: (20 May)                  │
│  └─ Payment Completed: ₹150 (18 May)             │
│                                                     │
└─────────────────────────────────────────────────────┘
```

### Booking Form
```
┌─────────────────────────────────────┐
│        NEW PARKING BOOKING           │
├─────────────────────────────────────┤
│ Organization: [VIIT Parking  ▼]    │
│ Parking Lot: [Ground Floor  ▼]     │
│ Available Slots: 35/100              │
│                                     │
│ Vehicle Number: [DL01AB1234]        │
│                                     │
│ Entry Date: [15-Jun-2024]           │
│ Entry Time: [10:00 AM ▼]            │
│                                     │
│ Exit Date: [15-Jun-2024]            │
│ Exit Time: [2:00 PM ▼]              │
│                                     │
│ Duration: 4 hours                   │
│ Rate: ₹50/hour                      │
│ Total: ₹200                         │
│                                     │
│ [Cancel]            [Confirm Booking]
└─────────────────────────────────────┘
```

### Organization Admin Dashboard
```
┌──────────────────────────────────────────────────┐
│ VIIT Parking Dashboard          [Settings] [^]  │
├──────────────────────────────────────────────────┤
│ Quick Stats:                                     │
│ ┌──────────┐ ┌──────────┐ ┌──────────┐          │
│ │Occupancy │ │Today's   │ │Total     │          │
│ │75% (375) │ │Revenue   │ │Members   │          │
│ │of 500    │ │₹2,250    │ │456       │          │
│ └──────────┘ └──────────┘ └──────────┘          │
│                                                 │
│ Parking Lots: [View All]                        │
│ Ground Floor: 85/100 occupied                   │
│ First Floor: 90/150 occupied                    │
│                                                 │
│ Recent Bookings:                                │
│ │ Time  │ Vehicle │ Duration │ Amount │ Status │
│ │10:05  │ DL01AB  │ 4h       │ ₹200   │ Active │
│ │09:30  │ MH02CD  │ 2h       │ ₹100   │ Done   │
│ └──────────────────────────────────────────────┘
│ [View Detailed Analytics]                       │
└──────────────────────────────────────────────────┘
```

### Watchman Portal
```
┌─────────────────────────────────────┐
│ Watchman Portal - Emp: WM001        │
├─────────────────────────────────────┤
│ [Scan QR Code]  [Manual Entry]      │
├─────────────────────────────────────┤
│                                     │
│ Recent Activity:                    │
│                                     │
│ ✓ Entry Marked: DL01AB1234         │
│   Vehicle: Maruti Swift             │
│   Time: 10:05 AM                    │
│                                     │
│ ⓘ Overstay Alert: MH02CD3456       │
│   Penalty: ₹50                      │
│   [Collect Payment]                 │
│                                     │
│ ✓ Exit Marked: KA03EF5678          │
│   Time: 02:10 PM                    │
│   Amount: ₹200 (Completed)          │
│                                     │
│ Active Vehicles: 45                 │
│ Available Slots: 125                │
│                                     │
└─────────────────────────────────────┘
```

### Payment Screen
```
┌──────────────────────────────────────┐
│        PAYMENT CONFIRMATION           │
├──────────────────────────────────────┤
│ Booking ID: #123                     │
│ Organization: VIIT Parking            │
│ Duration: 4 hours (10:00 - 14:00)    │
│                                      │
│ Amount Breakdown:                    │
│ ├─ Base Fare: ₹50 × 4 = ₹200        │
│ └─ Total: ₹200                       │
│                                      │
│ Payment Method:                      │
│ ⊙ UPI                               │
│ ○ Net Banking                       │
│ ○ Credit Card                       │
│ ○ Debit Card                        │
│ ○ Cash                              │
│                                      │
│ [Back]                [Pay Now]     │
└──────────────────────────────────────┘
```

---

## 🚀 Future Enhancements

### Phase 2 Features
- [ ] **Real-Time Map Integration**
  - Google Maps API for lot locations
  - GPS-based nearest parking finder
  - Real-time vehicle tracking on map

- [ ] **Mobile Application**
  - Native Android/iOS apps
  - Push notifications for bookings
  - Offline QR code access

- [ ] **Payment Gateway Integration**
  - Razorpay/PayPal integration
  - Real payment processing (vs. simulation)
  - Invoice generation and email

- [ ] **Email Notifications**
  - Booking confirmations
  - Payment receipts
  - Overstay alerts
  - Monthly statements

- [ ] **SMS Integration**
  - OTP verification via SMS
  - Booking updates
  - Payment confirmations

### Phase 3 Scalability
- [ ] **Database Migration**
  - PostgreSQL for production
  - Redis caching for performance
  - Database replication for redundancy

- [ ] **Cloud Deployment**
  - AWS EC2/RDS setup
  - Automated backups
  - CDN for static assets
  - Load balancing

- [ ] **Advanced Analytics**
  - Machine learning for demand prediction
  - Pricing optimization
  - Peak hour forecasting
  - Anomaly detection

- [ ] **IoT Integration**
  - Automatic gate control
  - ANPR (Automatic Number Plate Recognition)
  - Smart lighting based on occupancy
  - Sensor data integration

### Phase 4 Enterprise Features
- [ ] **Multi-Organization Support**
  - Network-wide analytics
  - Cross-organization transfers
  - Federated parking system

- [ ] **API Marketplace**
  - Third-party integration APIs
  - Webhook support
  - API authentication and rate limiting

- [ ] **SSSO Integration**
  - Corporate directory integration
  - OAuth 2.0 support
  - LDAP authentication

- [ ] **Accessibility**
  - Screen reader support
  - Multi-language support
  - WCAG 2.1 compliance

---

## 👥 Contributors

### Development Team

| Name | Role | Responsibilities |
|------|------|------------------|
| Shravani Kurkute | Full Stack Developer | Project initialization, architecture design, backend & frontend development |
| [Your Name] | Backend Developer | API development, database design |
| [Your Name] | Frontend Developer | UI/UX implementation, component development |
| [Your Name] | QA Engineer | Testing, bug fixes, documentation |

### Contribution Guidelines

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Roadmap

- ✅ **v1.0.0** - Basic parking management system
- 🔄 **v1.1.0** - UI/UX improvements, bug fixes
- 📋 **v2.0.0** - Mobile app, real payments, map integration
- 🎯 **v2.5.0** - Analytics dashboard, IoT integration
- 🌐 **v3.0.0** - Multi-organization network, enterprise features

---

## 📄 License

Park-Mitra is licensed under the **MIT License** - see the LICENSE file for details.

### What you can do:
- ✅ Commercial use
- ✅ Modification
- ✅ Distribution
- ✅ Private use
- ✅ Sublicensing

### Conditions:
- ⚠️ License and copyright notice must be included

### Limitations:
- ❌ No liability
- ❌ No warranty

**Full License Text:**
```
MIT License

Copyright (c) 2024 Shravani Kurkute

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🤝 Support & Contact

### Getting Help

- 📖 **Documentation**: Check the [API Documentation](#-api-documentation) section
- 🐛 **Report Bugs**: [GitHub Issues](https://github.com/Shravani-kurkute/Park-Mitra-Final/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/Shravani-kurkute/Park-Mitra-Final/discussions)

### Contact Information

| Channel | Details |
|---------|---------|
| Email | shravani@example.com |
| GitHub | [@Shravani-kurkute](https://github.com/Shravani-kurkute) |
| LinkedIn | [Shravani Kurkute](https://linkedin.com/in/shravani-kurkute) |
| Twitter | [@ShravaKurkute](https://twitter.com) |

### Feedback

We'd love to hear your feedback! Please:
1. 🌟 Star the repository if you find it useful
2. 📢 Share it with your network
3. 💌 Send feedback via email or GitHub discussions

---

## 📊 Project Statistics

- **Total Lines of Code**: ~3,500+
- **Backend Routes**: 7 main endpoints
- **Frontend Components**: 20+ reusable components
- **Database Tables**: 7 core + migration tables
- **API Endpoints**: 25+ endpoints
- **Test Coverage**: In progress
- **Development Time**: 3+ months

---

## 🎓 Learning Resources

### Technologies Covered
- Modern JavaScript ES6+
- React Hooks and Context API
- RESTful API Design
- SQLite Database Design
- Authentication & Authorization (JWT)
- Middleware Implementation
- Error Handling Patterns
- Rate Limiting & Security

### Recommended Reading
- [Express.js Guide](https://expressjs.com/)
- [React Documentation](https://react.dev/)
- [SQLite Docs](https://www.sqlite.org/docs.html)
- [JWT Guide](https://jwt.io/introduction)
- [RESTful API Best Practices](https://restfulapi.net/)

---




