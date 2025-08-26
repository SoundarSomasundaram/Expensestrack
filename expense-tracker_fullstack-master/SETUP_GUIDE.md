# 🗄️ Expense Tracker Database Setup Guide

This guide will help you set up the expense tracker application with MongoDB database connectivity.

## 📋 Prerequisites

1. **Node.js** (version 14 or higher)
2. **MongoDB** (local installation or MongoDB Atlas account)
3. **Git** (to clone/download the project)

## 🚀 Quick Setup

### Step 1: Install Dependencies

Navigate to the backend directory and install dependencies:

```bash
cd expense-tracker_fullstack-master/backend
npm install
```

### Step 2: Set Up Environment Variables

Create a `.env` file in the backend directory:

```bash
# Backend/.env
MONGO_URL=mongodb://localhost:27017/expense-tracker
PORT=5000
```

**For MongoDB Atlas (Cloud Database):**
```bash
MONGO_URL=mongodb+srv://your-username:your-password@your-cluster.mongodb.net/expense-tracker
PORT=5000
```

### Step 3: Start the Backend Server

```bash
cd expense-tracker_fullstack-master/backend
npm start
```

You should see:
```
Db Connected
listening to port: 5000
```

### Step 4: Open the Frontend

Open `expense-tracker-with-database.html` in your web browser. You should see a green "Connected to Database" indicator in the top-right corner.

## 🗄️ Database Configuration Options

### Option 1: Local MongoDB Installation

1. **Download MongoDB Community Server** from [mongodb.com](https://www.mongodb.com/try/download/community)
2. **Install MongoDB** following the installation wizard
3. **Start MongoDB service**:
   - Windows: MongoDB runs as a service automatically
   - Mac: `brew services start mongodb-community`
   - Linux: `sudo systemctl start mongod`

### Option 2: MongoDB Atlas (Cloud - Recommended)

1. **Create MongoDB Atlas Account** at [cloud.mongodb.com](https://cloud.mongodb.com)
2. **Create a new cluster** (free tier available)
3. **Get connection string**:
   - Click "Connect" on your cluster
   - Choose "Connect your application"
   - Copy the connection string
   - Replace `<password>` with your database user password
   - Replace `<dbname>` with `expense-tracker`

## 🔧 API Endpoints

The backend provides these REST API endpoints:

### Income Management
- `POST /api/v1/add-income` - Add new income
- `GET /api/v1/get-incomes` - Get all incomes
- `DELETE /api/v1/delete-income/:id` - Delete income by ID

### Expense Management
- `POST /api/v1/add-expense` - Add new expense
- `GET /api/v1/get-expenses` - Get all expenses
- `DELETE /api/v1/delete-expense/:id` - Delete expense by ID

## 📊 Database Schema

### Income Collection
```javascript
{
  _id: ObjectId,
  title: String (required, max 50 chars),
  amount: Number (required),
  type: String (default: "income"),
  date: Date (required),
  category: String (required),
  description: String (required, max 20 chars),
  createdAt: Date,
  updatedAt: Date
}
```

### Expense Collection
```javascript
{
  _id: ObjectId,
  title: String (required, max 50 chars),
  amount: Number (required),
  type: String (default: "expense"),
  date: Date (required),
  category: String (required),
  description: String (required, max 20 chars),
  createdAt: Date,
  updatedAt: Date
}
```

## 🛠️ Troubleshooting

### Connection Issues

1. **"Database Disconnected" message**:
   - Check if backend server is running on port 5000
   - Verify MongoDB connection string in `.env`
   - Ensure MongoDB service is running

2. **CORS errors**:
   - Backend includes CORS middleware
   - If issues persist, check browser console for specific errors

3. **Port already in use**:
   - Change PORT in `.env` file
   - Update API_BASE_URL in HTML file accordingly

### Database Issues

1. **MongoDB connection fails**:
   - Verify MongoDB is running: `mongo` or `mongosh`
   - Check connection string format
   - Ensure network access (for Atlas)

2. **Data not persisting**:
   - Check database permissions
   - Verify collection names match models

## 🔍 Viewing Database Data

### Using MongoDB Compass (GUI)
1. Download [MongoDB Compass](https://www.mongodb.com/try/download/compass)
2. Connect to your database
3. Navigate to `expense-tracker` database
4. View `incomes` and `expenses` collections

### Using MongoDB Shell
```bash
# Connect to database
mongo
# or
mongosh

# Switch to database
use expense-tracker

# View collections
show collections

# View all incomes
db.incomes.find()

# View all expenses
db.expenses.find()

# View formatted results
db.incomes.find().pretty()
```

## 📱 Features

### ✅ What Works with Database
- ✅ Add income/expense to database
- ✅ View all transactions from database
- ✅ Delete transactions from database
- ✅ Real-time connection status
- ✅ Error handling and user feedback
- ✅ Data persistence across sessions
- ✅ Automatic data refresh

### 🔄 Real-time Updates
- Connection status indicator
- Automatic data refresh after operations
- Loading states during operations
- Success/error messages

## 🚀 Deployment

### Backend Deployment
1. **Heroku**: Add MongoDB Atlas connection string
2. **Railway**: Connect GitHub repo and set environment variables
3. **Vercel**: Deploy Node.js backend with environment variables

### Frontend Deployment
1. **Netlify**: Upload HTML file
2. **Vercel**: Deploy static files
3. **GitHub Pages**: Host HTML file

**Remember to update the API_BASE_URL in the HTML file to match your deployed backend URL.**

## 📞 Support

If you encounter issues:
1. Check the browser console for errors
2. Verify backend server logs
3. Test API endpoints with Postman or similar tool
4. Ensure all environment variables are set correctly

---

**🎉 You're now ready to track expenses with a real database!**
