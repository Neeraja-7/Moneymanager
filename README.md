# 💰 Money Manager - Full Stack Application

A comprehensive personal finance management application built with **React**, **Node.js**, **Express**, and **MongoDB Atlas**.

![Money Manager](https://img.shields.io/badge/Money-Manager-green)
![React](https://img.shields.io/badge/React-19.x-blue)
![Node.js](https://img.shields.io/badge/Node.js-18.x-green)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-brightgreen)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-CSS-38B2AC)

---

## 📋 Table of Contents

1. [Features](#-features)
2. [Tech Stack](#-tech-stack)
3. [Prerequisites](#-prerequisites)
4. [Project Structure](#-project-structure)
5. [Step-by-Step Setup Guide](#-step-by-step-setup-guide)
6. [API Documentation](#-api-documentation)
7. [Database Schema](#-database-schema)
8. [Troubleshooting](#-troubleshooting)

---

## ✨ Features

### 📊 Dashboard
- Weekly, Monthly, and Yearly income/expense views
- Interactive Bar & Pie charts
- Account balances overview
- Net balance calculation

### 💳 Transaction Management
- Add income and expenses with modal popup
- One-line description for each transaction
- **Categories**: Fuel, Food, Movie, Loan, Medical, Shopping, Transport, Utilities, Entertainment, Salary, Freelance, Investment, Gift, Other
- **Divisions**: Office & Personal (e.g., Fuel for office vs personal use)
- Date & time tracking
- **Edit transactions within 12 hours only** (restricted after)
- Delete transactions

### 🔍 Filtering & Search
- Filter by type (Income/Expense)
- Filter by category
- Filter by division (Office/Personal)
- **Date range filtering** - Track income/expense between two dates
- Filter by account

### 💰 Account Management
- Multiple accounts (Cash, Bank, Credit Card, Savings)
- Transfer money between accounts
- Transfer history

### 📈 Summary & Reports
- Category-wise summary with charts
- Income vs Expense analysis
- Visual pie charts and breakdown tables

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| React 19 | UI Library |
| TypeScript | Type Safety |
| Vite | Build Tool |
| Tailwind CSS | Styling |
| Recharts | Charts & Graphs |
| Lucide React | Icons |
| Date-fns | Date Manipulation |

### Backend
| Technology | Purpose |
|------------|---------|
| Node.js | Runtime Environment |
| Express.js | Web Framework |
| MongoDB Atlas | Cloud Database |
| Mongoose | ODM (Object Data Modeling) |
| CORS | Cross-Origin Resource Sharing |
| Dotenv | Environment Variables |

---

## 📋 Prerequisites

Before you begin, ensure you have:

- **Node.js** (v18.x or higher) - [Download Here](https://nodejs.org/)
- **npm** (v9.x or higher) - Comes with Node.js
- **MongoDB Atlas Account** - [Sign Up Free](https://www.mongodb.com/cloud/atlas)
- **Git** (optional) - [Download Here](https://git-scm.com/)

### Verify Installation

Open your terminal and run:

```bash
node --version
# Should show: v18.x.x or higher

npm --version
# Should show: 9.x.x or higher
```

---

## 📁 Project Structure

```
money-manager/
│
├── 📂 backend/                 # Node.js Backend
│   ├── 📂 config/
│   │   └── database.js        # MongoDB connection
│   ├── 📂 controllers/
│   │   ├── accountController.js
│   │   ├── transactionController.js
│   │   └── transferController.js
│   ├── 📂 middleware/
│   │   └── errorHandler.js
│   ├── 📂 models/
│   │   ├── Account.js
│   │   ├── Transaction.js
│   │   └── Transfer.js
│   ├── 📂 routes/
│   │   ├── accounts.js
│   │   ├── transactions.js
│   │   └── transfers.js
│   ├── .env.example           # Environment template
│   ├── package.json
│   ├── seedData.js            # Database seeder
│   └── server.js              # Express server
│
├── 📂 src/                     # React Frontend
│   ├── 📂 components/
│   │   ├── AccountTransfer.tsx
│   │   ├── Dashboard.tsx
│   │   ├── Filters.tsx
│   │   ├── Summary.tsx
│   │   ├── TransactionList.tsx
│   │   └── TransactionModal.tsx
│   ├── 📂 context/
│   │   └── MoneyContext.tsx
│   ├── 📂 data/
│   │   └── initialData.ts
│   ├── 📂 services/
│   │   └── api.ts             # API service layer
│   ├── 📂 types/
│   │   └── index.ts
│   ├── 📂 utils/
│   │   ├── cn.ts
│   │   └── helpers.ts
│   ├── App.tsx
│   ├── index.css
│   └── main.tsx
│
├── index.html
├── package.json
├── README.md
├── tailwind.config.js
├── tsconfig.json
└── vite.config.ts
```

---

## 🚀 Step-by-Step Setup Guide

### Step 1: Download/Clone the Project

```bash
# Create a new folder and extract the project files there
# OR if using Git:
git clone <repository-url>
cd money-manager
```

### Step 2: Set Up MongoDB Atlas (Free Cloud Database)

#### 2.1 Create MongoDB Atlas Account

1. Go to [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2. Click **"Try Free"** and sign up with email or Google
3. Complete the registration process

#### 2.2 Create a New Cluster

1. After login, click **"Build a Database"**
2. Select **"M0 FREE"** tier (Shared - Free Forever)
3. Choose your cloud provider (AWS recommended)
4. Select a region closest to you
5. Click **"Create"** (takes 1-3 minutes to provision)

#### 2.3 Create Database User

1. In the left sidebar, click **"Database Access"**
2. Click **"Add New Database User"**
3. Choose **"Password"** authentication
4. Enter:
   - Username: `moneymanager`
   - Password: `your_secure_password` (click "Autogenerate Secure Password" and SAVE IT!)
5. Under **"Database User Privileges"**, select **"Read and write to any database"**
6. Click **"Add User"**

#### 2.4 Configure Network Access

1. In the left sidebar, click **"Network Access"**
2. Click **"Add IP Address"**
3. Click **"Allow Access from Anywhere"** (adds 0.0.0.0/0)
   - ⚠️ For production, add only your specific IP
4. Click **"Confirm"**

#### 2.5 Get Your Connection String

1. In the left sidebar, click **"Database"**
2. Click **"Connect"** on your cluster
3. Select **"Connect your application"**
4. Choose Driver: **Node.js** and Version: **5.5 or later**
5. Copy the connection string. It looks like:
   ```
   mongodb+srv://moneymanager:<password>@cluster0.xxxxx.mongodb.net/?retryWrites=true&w=majority
   ```
6. **Replace `<password>`** with your actual password from step 2.3

### Step 3: Set Up the Backend

Open a terminal and run:

```bash
# Navigate to backend folder
cd backend

# Install dependencies
npm install

# Create environment file
# On Mac/Linux:
cp .env.example .env

# On Windows:
copy .env.example .env
```

Now edit the `.env` file with your MongoDB connection string:

```bash
# Open .env in a text editor (VS Code, Notepad++, etc.)
# Edit it to look like this:

PORT=5000
NODE_ENV=development
MONGODB_URI=mongodb+srv://moneymanager:YOUR_ACTUAL_PASSWORD@cluster0.xxxxx.mongodb.net/moneymanager?retryWrites=true&w=majority
```

⚠️ **Important**: 
- Replace `YOUR_ACTUAL_PASSWORD` with your real password
- Replace `cluster0.xxxxx` with your actual cluster address
- Add `/moneymanager` before the `?` to specify the database name

### Step 4: Set Up the Frontend

Open a **new terminal** and run:

```bash
# Navigate to the root project folder (not backend)
cd ..   # if you're still in backend folder

# Install frontend dependencies
npm install
```

### Step 5: Seed the Database (Optional but Recommended)

This adds sample data to your database:

```bash
# In the backend folder
cd backend
npm run seed
```

You should see:
```
📦 Connected to MongoDB
🗑️  Cleared existing data
✅ Accounts created
✅ 90 transactions created
✅ 10 transfers created
🎉 Database seeded successfully!
```

### Step 6: Start the Backend Server

In the **backend** terminal:

```bash
cd backend
npm run dev
```

You should see:
```
🚀 Server running on port 5000
📍 API available at http://localhost:5000/api
📦 Connected to MongoDB Atlas: cluster0-shard-00-00.xxxxx.mongodb.net
```

### Step 7: Start the Frontend

In a **new terminal** (keep backend running):

```bash
# In the root project folder
npm run dev
```

You should see:
```
  VITE v5.x.x  ready in xxx ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

### Step 8: Open the Application

1. Open your browser
2. Go to **http://localhost:5173**
3. 🎉 **You should see the Money Manager dashboard!**

---

## 🔄 Quick Start Commands Summary

```bash
# Terminal 1 - Backend
cd backend
npm install
cp .env.example .env    # Then edit .env with your MongoDB URI
npm run seed            # Optional: Add sample data
npm run dev             # Start backend server

# Terminal 2 - Frontend
npm install
npm run dev             # Start frontend
```

---

## 📡 API Documentation

### Base URL
```
http://localhost:5000/api
```

### Endpoints

#### Transactions
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/transactions` | Get all transactions |
| `GET` | `/transactions/:id` | Get single transaction |
| `POST` | `/transactions` | Create transaction |
| `PUT` | `/transactions/:id` | Update transaction (within 12 hours) |
| `DELETE` | `/transactions/:id` | Delete transaction |
| `GET` | `/transactions/filter?type=expense&category=food` | Filter transactions |
| `GET` | `/transactions/summary` | Get category summary |
| `GET` | `/transactions/stats?period=monthly` | Get dashboard stats |

#### Accounts
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/accounts` | Get all accounts |
| `GET` | `/accounts/:id` | Get single account |
| `POST` | `/accounts/init` | Initialize default accounts |
| `GET` | `/accounts/total` | Get total balance |

#### Transfers
| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/transfers` | Get all transfers |
| `POST` | `/transfers` | Create transfer |
| `GET` | `/transfers/account/:id` | Get transfers by account |

### Example API Requests

**Create a new expense:**
```bash
curl -X POST http://localhost:5000/api/transactions \
  -H "Content-Type: application/json" \
  -d '{
    "type": "expense",
    "amount": 50,
    "category": "food",
    "division": "personal",
    "description": "Lunch at restaurant",
    "accountId": "cash"
  }'
```

**Transfer between accounts:**
```bash
curl -X POST http://localhost:5000/api/transfers \
  -H "Content-Type: application/json" \
  -d '{
    "fromAccountId": "bank",
    "toAccountId": "cash",
    "amount": 200,
    "description": "ATM withdrawal"
  }'
```

---

## 🗄️ Database Schema

### Transaction
```javascript
{
  _id: ObjectId,
  type: "income" | "expense",
  amount: Number,
  category: String,      // fuel, food, movie, loan, medical, etc.
  division: "office" | "personal",
  description: String,
  date: Date,
  accountId: "cash" | "bank" | "credit" | "savings",
  createdAt: Date,
  updatedAt: Date
}
```

### Account
```javascript
{
  _id: "cash" | "bank" | "credit" | "savings",
  name: String,
  balance: Number,
  icon: String,
  color: String
}
```

### Transfer
```javascript
{
  _id: ObjectId,
  fromAccountId: String,
  toAccountId: String,
  amount: Number,
  description: String,
  date: Date,
  createdAt: Date
}
```

---

## 🔧 Troubleshooting

### ❌ MongoDB Connection Error
```
Error: MongoNetworkError: failed to connect to server
```
**Solutions:**
1. Check if your IP is whitelisted in MongoDB Atlas → Network Access
2. Verify the connection string in `.env` is correct
3. Make sure password doesn't have special characters (or URL-encode them)
4. Check if MongoDB Atlas cluster is active (not paused)

### ❌ CORS Error
```
Access to XMLHttpRequest blocked by CORS policy
```
**Solutions:**
1. Make sure backend is running on port 5000
2. Verify frontend is running on port 5173
3. Check `server.js` has correct CORS origins

### ❌ Port Already in Use
```
Error: listen EADDRINUSE: address already in use :::5000
```
**Solutions:**
```bash
# Mac/Linux - Find and kill process
lsof -i :5000
kill -9 <PID>

# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F
```

### ❌ Module Not Found
```
Error: Cannot find module 'xxx'
```
**Solutions:**
```bash
# Delete node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

### ❌ Transaction Edit Disabled
The app shows "Edit disabled" - This is by design! Transactions can only be edited within 12 hours of creation.

---

## 🧪 Testing the Connection

### Test Backend
Open browser: `http://localhost:5000/api/health`

You should see:
```json
{
  "success": true,
  "message": "Money Manager API is running",
  "timestamp": "2024-01-15T10:30:00.000Z"
}
```

### Test Frontend → Backend Connection
1. Open browser console (F12 → Console)
2. Navigate around the app
3. You should see network requests to `localhost:5000`

---

## 📱 Application Features Demo

### Dashboard
- View income vs expense charts
- Toggle between Weekly/Monthly/Yearly views
- See account balances at a glance

### Add Transaction
1. Click the green **"Add Transaction"** button
2. Switch between **Income** and **Expense** tabs
3. Fill in: Amount, Description, Category, Division, Account, Date
4. Click Add

### Filter Transactions
1. Go to **Transactions** tab
2. Use dropdown filters: Type, Division, Category, Account
3. Use date range picker for specific periods

### Transfer Money
1. Go to **Transfers** tab
2. Select source and destination accounts
3. Enter amount and description
4. Click **Transfer Money**

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙏 Built With

- [React](https://reactjs.org/)
- [Vite](https://vitejs.dev/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Express.js](https://expressjs.com/)
- [MongoDB](https://www.mongodb.com/)
- [Mongoose](https://mongoosejs.com/)
- [Recharts](https://recharts.org/)
- [Lucide Icons](https://lucide.dev/)

---

⭐ **Star this repository if you found it helpful!**

📧 **Questions?** Open an issue!
