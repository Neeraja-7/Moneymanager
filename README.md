
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
