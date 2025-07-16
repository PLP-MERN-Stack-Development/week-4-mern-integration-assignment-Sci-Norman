# 🪟 Windows Setup Guide for MERN Blog Application

## 🚨 **Fixed Issues:**
- ✅ Updated `multer` version from `1.4.5` to `1.4.4` (correct version)
- ✅ Updated `mongoose` version for better compatibility
- ✅ Added Windows PowerShell compatible commands
- ✅ Pre-configured with your MongoDB Atlas connection string

## 📦 **Windows Setup Instructions:**

### **Step 1: Extract the Application**
```powershell
# Extract the zip file to your desired location
# Example: C:\Users\YourName\Downloads\mern-blog-application
```

### **Step 2: Install Server Dependencies**
```powershell
# Navigate to server directory
cd server

# Install dependencies
npm install

# If you get permission errors, run PowerShell as Administrator
```

### **Step 3: Install Client Dependencies**
```powershell
# Navigate to client directory (from project root)
cd client

# Install dependencies
npm install
```

### **Step 4: Environment Variables (Already Configured)**
Your MongoDB Atlas connection string is already configured in `server/.env`:
```env
PORT=5000
MONGODB_URI=mongodb+srv://Norman:Blog@cluster0.eqx9xnc.mongodb.net/blogDB?retryWrites=true&w=majority&appName=Cluster0
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
NODE_ENV=development
```

**For Client (.env.local):**
```powershell
# In client directory, create .env.local
copy .env.example .env.local
```

### **Step 5: Run the Applications**

**Option 1: Using separate PowerShell windows**
```powershell
# Terminal 1 - Backend (in server directory)
npm run dev

# Terminal 2 - Frontend (in client directory)  
npm run dev
```

**Option 2: Using PowerShell with background processes**
```powershell
# From project root directory
Start-Process powershell -ArgumentList "-NoExit", "-Command", "cd server; npm run dev"
Start-Process powershell -ArgumentList "-NoExit", "-Command", "cd client; npm run dev"
```

### **Step 6: Access the Application**
- **Frontend:** http://localhost:3000
- **Backend API:** http://localhost:5000
- **Health Check:** http://localhost:5000/api/health

## 🔧 **Troubleshooting:**

### **PowerShell Execution Policy Issues:**
```powershell
# If you get execution policy errors
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### **Node.js/npm Issues:**
```powershell
# Check Node.js version (should be 16+)
node --version

# Check npm version
npm --version

# Clear npm cache if needed
npm cache clean --force
```

### **Port Already in Use:**
```powershell
# Find process using port 5000
netstat -ano | findstr :5000

# Kill process by PID (replace XXXX with actual PID)
taskkill /PID XXXX /F
```

## 🎯 **Quick Start Commands (Copy & Paste):**
```powershell
# Setup (run once)
cd server
npm install
cd ../client
npm install

# Daily development (run these in separate terminals)
# Terminal 1:
cd server
npm run dev

# Terminal 2:
cd client
npm run dev
```

## 📝 **Notes:**
- Your MongoDB Atlas connection is already configured
- The application uses port 3000 for frontend and 5000 for backend
- Make sure both ports are available
- No need to install MongoDB locally - it's using Atlas
