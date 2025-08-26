# Backend Setup Guide

## Quick Start

### 1. Navigate to Backend Directory
```bash
cd backend
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Set Up Environment Variables
Create a `.env` file in the backend directory:
```env
MONGO_URL=mongodb://localhost:27017/expense-tracker
PORT=5000
```

### 4. Start MongoDB (if not running)
- **Windows**: Start MongoDB service or run `mongod`
- **Mac**: `brew services start mongodb-community`
- **Linux**: `sudo systemctl start mongod`

### 5. Start the Server
```bash
npm start
```

The server will start on `http://localhost:5000`

## Alternative: Use MongoDB Atlas (Cloud)

If you don't have MongoDB installed locally:

1. Go to [MongoDB Atlas](https://www.mongodb.com/atlas)
2. Create a free account and cluster
3. Get your connection string
4. Replace the MONGO_URL in `.env` with your Atlas connection string

## Test the API

Once the server is running, test these endpoints:
- `GET http://localhost:5000/api/v1/get-incomes`
- `GET http://localhost:5000/api/v1/get-expenses`

## Troubleshooting

### Port Already in Use
If port 5000 is busy, change the PORT in `.env`:
```env
PORT=3001
```

### MongoDB Connection Issues
- Make sure MongoDB is running
- Check your connection string
- For Atlas: Ensure your IP is whitelisted

### CORS Issues
The backend is configured to allow requests from any origin. If you have issues, check the CORS settings in `app.js`.
