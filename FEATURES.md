# Air Quality Monitor - Updated Documentation

## New Features Added

### 1. User Authentication System
- **Register**: Create a new user account with username, email, and password
- **Login**: Secure login with JWT token-based authentication
- All routes are protected and require authentication

### 2. Notification Preferences System
Each user can now set custom notification preferences:
- **Add Notification Preferences**: Choose a city and set AQI threshold
- **Manage Preferences**: 
  - Enable/Disable notifications per city
  - Update AQI threshold for each city
  - Delete preferences
- **Real-time Notification Checking**: System checks if current AQI exceeds user's threshold

### 3. User Dashboard Features
- Welcome message with username
- Navigation bar with quick access to settings
- Logout functionality
- Protected routes ensure only logged-in users can access

## Backend Setup

### Database Models
- **User**: Stores user credentials (username, email, password)
- **NotificationPreference**: Stores each user's notification settings per city

### API Endpoints

#### Authentication Routes (`/api/auth/`)
- `POST /register` - Create new user account
- `POST /login` - Login and get JWT token
- `GET /me` - Get current user info (requires auth)

#### Notification Routes (`/api/notifications/`)
- `GET /preferences` - Get all preferences for current user
- `POST /preferences` - Create new preference
- `PUT /preferences/<id>` - Update existing preference
- `DELETE /preferences/<id>` - Delete preference
- `GET /check` - Check if notification should be sent

### Installation & Running

1. Install dependencies:
```bash
cd backend
pip install -r requirements.txt
```

2. Run the Flask server:
```bash
python app.py
```

The server will run on `http://localhost:5000` and automatically create the SQLite database.

## Frontend Setup

### New Components
- **Login.js**: User login page
- **Register.js**: User registration page
- **NotificationSettings.js**: Manage notification preferences
- **ProtectedRoute.js**: Route protection component

### Installation & Running

1. Install dependencies:
```bash
cd frontend
npm install
```

2. Start the React app:
```bash
npm start
```

The app will run on `http://localhost:3000`

## User Flow

1. **First Time User**:
   - Navigate to `/register`
   - Create account with username, email, password
   - Automatically logged in after registration

2. **Returning User**:
   - Go to `/login`
   - Enter credentials
   - Access dashboard

3. **Set Notifications**:
   - Click "Notification Settings" button in navbar
   - Add preferences for cities you care about
   - Set AQI thresholds (recommended: 100)
   - Enable/disable as needed

4. **Dashboard**:
   - View current air quality
   - See 7-day trends
   - Check pollutant levels
   - Quick access to settings

## Security Features

- Passwords are hashed using Flask-Bcrypt
- JWT tokens expire after 30 days
- Protected routes prevent unauthorized access
- User can only modify their own preferences

## Default AQI Thresholds Guide

- **Good** (0-50): No action needed
- **Moderate** (51-100): Sensitive individuals should limit outdoor activity
- **Unhealthy for Sensitive Groups** (101-150): Recommended limit for general population
- **Unhealthy** (151-200): Start limiting outdoor activity
- **Very Unhealthy** (201-300): Avoid outdoor activity
- **Hazardous** (300+): Stay indoors, use air purifiers

## Environment Variables

For production, change in `app.py`:
```python
app.config['JWT_SECRET_KEY'] = 'your-secure-secret-key'
```

## Database

SQLite database (`airquality.db`) is automatically created in the backend directory with tables:
- `users`
- `notification_preferences`
