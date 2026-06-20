# Air Quality Monitor - Real-Time Dashboard

A modern web application to monitor air quality levels in real-time with personalized health recommendations and trend analysis.

![Air Quality Monitor](./screenshot.png)

## 🌟 Features

- **Real-Time AQI Monitoring**: Get instant updates on Air Quality Index for any city
- **Comprehensive Pollutant Data**: View detailed levels of PM2.5, PM10, NO2, SO2, CO, and O3
- **Health Recommendations**: Personalized health advice based on air quality levels
- **Air Quality Trends**: Visual graphs showing AQI trends over time
- **City Search**: Search for air quality data for any city worldwide
- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices

## 📋 Prerequisites

- Python 3.7+
- Node.js 14+
- npm or yarn

## 🚀 Installation

### Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Install Python dependencies:
```bash
pip install -r requirements.txt
```

3. Run the Flask server:
```bash
python app.py
```

The backend will start on `http://127.0.0.1:5000`

### Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install Node dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm start
```

The frontend will open on `http://localhost:3000`

## 📂 Project Structure

```
air-quality-monitor/
├── backend/
│   ├── app.py              # Flask API server
│   └── requirements.txt     # Python dependencies
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   └── Dashboard.js    # Main dashboard component
│   │   ├── styles/
│   │   │   └── Dashboard.css   # Dashboard styling
│   │   ├── App.js              # Main app component
│   │   ├── App.css             # App styling
│   │   └── index.js            # React entry point
│   ├── package.json
│   └── README.md
└── README.md (this file)
```

## 🔌 API Endpoints

### Get Air Quality Data
- **Endpoint**: `GET /get-aqi`
- **Parameters**: 
  - `city` (string): City name (default: "Kuala Lumpur")
- **Response**:
```json
{
  "city": "Kuala Lumpur",
  "country": "Malaysia",
  "aqi": 85,
  "status": {
    "status": "Moderate",
    "color": "#ffff00"
  },
  "lastUpdated": "Just now",
  "pollutants": {
    "pm25": 35.2,
    "pm10": 65,
    "no2": 28,
    "so2": 12,
    "co": 0.8,
    "o3": 45
  },
  "trend": [
    {"day": "Mon", "aqi": 80},
    {"day": "Tue", "aqi": 85},
    ...
  ]
}
```

### Get Available Cities
- **Endpoint**: `GET /get-cities`
- **Response**:
```json
{
  "cities": ["Kuala Lumpur", "Dubai", "New York", "London", "Tokyo", ...]
}
```

## 🎨 Dashboard Features

### Header
- Search bar to query cities
- "Get Current Location" button for location-based search
- "Search by Comparison" button for comparing cities

### Air Quality Index
- Circular progress indicator showing AQI value
- Color-coded status (Good, Moderate, Unhealthy, etc.)

### Pollutants Cards
- PM2.5, PM10, NO2, SO2, CO, O3 levels
- Color-coded indicators based on pollution levels
- Units displayed (µg/m³ or ppb)

### Health Recommendations
- Warning alerts for sensitive groups
- Preventive measures
- Best practices for air quality

### Air Quality Trends
- Line chart showing AQI trends over 7 days
- Time period selection (7-Hours, 7-Days, 1-Month)

## 🎯 AQI Status Levels

| AQI Range | Status | Color | Health Impact |
|-----------|--------|-------|----------------|
| 0-50 | Good | Green | No health effects expected |
| 51-100 | Moderate | Yellow | Minor breathing problems for sensitive groups |
| 101-150 | Unhealthy for Sensitive Groups | Orange | Noticeable increase in respiratory problems |
| 151-200 | Unhealthy | Red | General public begins to experience problems |
| 201-300 | Very Unhealthy | Purple | Severe health effects |
| 301+ | Hazardous | Maroon | Life-threatening for all groups |

## 🔧 Technologies Used

### Frontend
- React 19
- Recharts for data visualization
- CSS3 for styling
- Fetch API for HTTP requests

### Backend
- Flask 2.3.2
- Flask-CORS for cross-origin requests
- Python 3.7+

## 💡 Usage

1. Open the application in your browser (usually http://localhost:3000)
2. The dashboard will load with default data for Kuala Lumpur
3. Enter a city name in the search bar and click "Search" to fetch data for that city
4. View the AQI, pollutant levels, health recommendations, and trends
5. Health recommendations will update based on the current air quality

## 🔄 How It Works

1. **Frontend**: React component fetches data from the backend API
2. **Backend**: Flask server generates air quality data (simulated with random values)
3. **Display**: Data is visualized using charts and color-coded indicators
4. **Updates**: Real-time data updates when searching for different cities

## 📱 Responsive Breakpoints

- **Desktop**: 1024px and above
- **Tablet**: 768px - 1023px
- **Mobile**: Below 768px

## 🐛 Troubleshooting

### Backend won't start
- Ensure Python 3.7+ is installed
- Install requirements: `pip install -r requirements.txt`
- Check if port 5000 is available

### Frontend won't load
- Ensure Node.js is installed
- Run `npm install` to install dependencies
- Clear browser cache and reload

### CORS errors
- Backend Flask-CORS is enabled by default
- Ensure backend is running on http://127.0.0.1:5000
- Check browser console for specific error messages

## 📝 Future Enhancements

- [ ] Integration with real AQI data APIs
- [ ] User authentication and saved locations
- [ ] Historical data analysis
- [ ] Weather integration
- [ ] Mobile app version
- [ ] Real-time notifications
- [ ] Multiple language support

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📧 Contact

For questions or feedback, please open an issue on the GitHub repository.

---

**Note**: This application currently uses simulated data for demonstration purposes. To use real-world air quality data, integrate with services like OpenWeatherMap API or AirVisual API.
