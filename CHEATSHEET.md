# 🌍 Air Quality Monitor - Project Cheatsheet

## 📋 Project Overview
Real-time air quality monitoring application using OpenWeather API. Users can search cities, view AQI levels, and set notification preferences.

---

## 🛠️ Tech Stack

### **Backend**
- **Framework:** Flask
- **Database:** SQLite (flask-sqlalchemy)
- **External API:** OpenWeather Air Pollution & Geo APIs
- **Port:** `8000`

### **Frontend**
- **Framework:** React 19
- **Routing:** React Router v6
- **Charts:** Recharts
- **HTTP Client:** Fetch API
- **Port:** `3000`

### **Dependencies Removed**
- ❌ Flask-JWT-Extended (JWT authentication)
- ❌ Flask-BCrypt (password hashing)
- ❌ User authentication system

---

## 🗂️ Project Structure

```
air-quality-monitor/
├── backend/
│   ├── app.py                  # Main Flask app, AQI routes
│   ├── models.py               # Database models (NotificationPreference)
│   ├── routes_notifications.py # Notification CRUD endpoints
│   ├── requirements.txt        # Python dependencies
│   ├── instance/               # SQLite database folder
│   └── .env                    # Environment variables (OPENWEATHER_API_KEY)
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── App.js              # Main router
│   │   ├── index.js            # React entry point
│   │   ├── index.css           # Global styles
│   │   ├── components/
│   │   │   ├── Dashboard.js    # Main AQI display page
│   │   │   └── NotificationSettings.js  # Notification preferences
│   │   └── styles/
│   │       ├── Dashboard.css
│   │       ├── NotificationSettings.css
│   │       └── Auth.css        # (Unused - kept for reference)
│   ├── package.json
│   └── .gitignore
│
├── FEATURES.md    # Feature documentation
├── README.md      # Project readme
├── TODO.md        # Task tracking
└── CHEATSHEET.md  # This file
```

---

## 🔑 Key Changes Made

### **Backend Changes**
1. ✅ Removed `routes_auth.py` file
2. ✅ Removed `User` model from `models.py`
3. ✅ Removed JWT & BCrypt imports
4. ✅ Updated `routes_notifications.py` - removed `@jwt_required()` decorators
5. ✅ Added database initialization in `app.py`
6. ✅ Registered notification blueprint in `app.py`

### **Frontend Changes**
1. ✅ Deleted `Login.js` component
2. ✅ Deleted `Register.js` component
3. ✅ Deleted `ProtectedRoute.js` component
4. ✅ Updated `Dashboard.js` - removed auth logic & logout button
5. ✅ Updated `NotificationSettings.js` - removed JWT headers & auth checks
6. ✅ Changed API endpoint to `http://127.0.0.1:8000`

---

## 🌐 API Endpoints

### **AQI Endpoints (Public)**
```
GET  /                    # Backend status
GET  /get-aqi?city=Karachi
GET  /get-cities?q=search_query
```

### **Notification Endpoints (No Auth Required)**
```
GET    /api/notifications/preferences          # Get all preferences
POST   /api/notifications/preferences          # Create preference
PUT    /api/notifications/preferences/<id>    # Update preference
DELETE /api/notifications/preferences/<id>    # Delete preference
GET    /api/notifications/check               # Check if notify
```

---

## 📦 Database Schema

### **NotificationPreference Table**
```sql
id              INTEGER PRIMARY KEY
city            VARCHAR(100) NOT NULL
aqi_threshold   INTEGER DEFAULT 100
is_enabled      BOOLEAN DEFAULT TRUE
created_at      DATETIME
updated_at      DATETIME
```

---

## 🚀 How to Run

### **Backend**
```bash
cd backend
pip install -r requirements.txt
python app.py
# Server runs on: http://127.0.0.1:8000
```

### **Frontend**
```bash
cd frontend
npm install
npm start
# App opens on: http://localhost:3000
```

---

## 📝 Environment Variables

### **Backend (.env file)**
```
OPENWEATHER_API_KEY=your_api_key_here
```

Get API key from: https://openweathermap.org/api

---

## 🎯 Features

### **Dashboard Page (/)** 
- 🔍 Search cities by name
- 📊 Real-time AQI display with circular gauge
- 📈 Pollutants: PM2.5, PM10, CO, NO₂, O₃, SO₂
- 📉 Trend graphs (7 Hours, 7 Days, 1 Month)
- 💓 Health recommendations based on AQI
- ⚙️ Navigation to Notification Settings

### **Notification Settings (/notifications)**
- ➕ Create notification preferences for cities
- 🎯 Set AQI thresholds (0-300)
- 📋 List all preferences
- ✏️ Update thresholds with slider
- 🗑️ Delete preferences
- 🔘 Toggle preferences on/off

---

## 🐛 Current Status

✅ **Working:**
- Real OpenWeather API integration
- City search
- AQI calculations and display
- Notification preferences CRUD
- Database persistence
- CORS enabled

❌ **Removed (Intentionally):**
- User authentication
- Login/Register pages
- JWT tokens
- User-specific data

---

## 📊 AQI Scale

```
0-50     → GOOD                           🟢
51-100   → MODERATE                       🟡
101-150  → UNHEALTHY FOR SENSITIVE       🟠
151-200  → UNHEALTHY                      🔴
201-300  → VERY UNHEALTHY                 🟣
300+     → HAZARDOUS                      ⚫
```

---

## 🔧 Quick Debugging

### **Frontend API Issues?**
- Ensure backend running on `http://127.0.0.1:8000`
- Check browser console for error messages
- Verify OpenWeather API key in backend .env

### **Database Issues?**
- Delete `instance/` folder to reset database
- Check `backend.log` for errors

### **CORS Errors?**
- CORS already enabled for all origins in `app.py`
- Check if ports match (3000 frontend, 8000 backend)

---

## 📱 Port Reference

| Service | Port | URL |
|---------|------|-----|
| Frontend | 3000 | http://localhost:3000 |
| Backend | 8000 | http://127.0.0.1:8000 |
| Database | N/A | instance/air_quality.db |

---

## 💾 File Operations

### **View all preferences**
```bash
# Through API
curl http://127.0.0.1:8000/api/notifications/preferences
```

### **Check database**
```bash
# SQLite CLI
sqlite3 backend/instance/air_quality.db
.tables  # View tables
SELECT * FROM notification_preference;
```

---

## 📞 Notes

- **No login required** - Anyone can use the app
- **No user data stored** - Only global notification preferences
- **Live API** - Real-time AQI data from OpenWeather
- **Stateless backend** - No sessions or tokens needed

---

## 🎓 What Was Used in This Project

| Feature | Technology |
|---------|-----------|
| Frontend Framework | React 19 |
| State Management | React Hooks (useState, useEffect) |
| Routing | React Router v6 |
| API Calls | Fetch API |
| Charts | Recharts |
| Backend | Flask |
| Database | SQLite + SQLAlchemy |
| External API | OpenWeather (Geo + Air Pollution) |
| CORS | Flask-CORS |
| Environment | python-dotenv |
| HTTP Method | REST |

---

## 🔗 Useful Links

- OpenWeather API: https://openweathermap.org/api/air-pollution
- React Documentation: https://react.dev
- Flask Documentation: https://flask.palletsprojects.com
- Recharts: https://recharts.org

---

**Last Updated:** January 23, 2026  
**Status:** ✅ Production Ready (No Auth)
