# Module 05: Project - Weather Dashboard

## Level 2.4: JavaScript Advanced

---

## Project Overview

Build a **Weather Dashboard** application that fetches real weather data and displays it beautifully!

---

## Project Requirements

### Must Have (Required)

| Feature | Skills Demonstrated |
|---------|---------------------|
| Search by city name | DOM manipulation, events |
| Display current weather | API fetching, async/await |
| Show temperature, humidity, conditions | Data processing |
| Weather icons | Conditional rendering |
| Error handling | Try/catch, user feedback |
| Loading states | UX, async handling |
| Responsive design | CSS skills |

### Nice to Have (Bonus)

| Feature | Skills Shown |
|---------|--------------|
| 5-day forecast | API, data processing |
| Geolocation | Browser APIs |
| Recent searches | localStorage |
| Temperature unit toggle | State management |
| Background based on weather | Dynamic styling |

---

## Getting Started

### 1. Get API Key

Sign up at [OpenWeatherMap](https://openweathermap.org/api) for a free API key.

### 2. Project Structure

```
weather-dashboard/
├── index.html
├── css/
│ └── style.css
└── js/
 └── app.js
```

---

## Step 1: HTML Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Weather Dashboard</title>
 <link rel="stylesheet" href="css/style.css">
</head>
<body>
 <div class="container">
 <header>
 <h1> Weather Dashboard</h1>
 </header>
 
 <main>
 <!-- Search Section -->
 <section class="search-section">
 <form id="search-form">
 <input 
 type="text" 
 id="city-input" 
 placeholder="Enter city name..."
 autocomplete="off"
 >
 <button type="submit">Search</button>
 </form>
 </section>
 
 <!-- Loading State -->
 <div id="loading" class="loading hidden">
 <div class="spinner"></div>
 <p>Loading weather data...</p>
 </div>
 
 <!-- Error State -->
 <div id="error" class="error hidden">
 <p id="error-message"></p>
 <button id="retry-btn">Try Again</button>
 </div>
 
 <!-- Weather Display -->
 <section id="weather-display" class="weather-display hidden">
 <div class="current-weather">
 <div class="weather-header">
 <h2 id="city-name">City Name</h2>
 <p id="date">Date</p>
 </div>
 
 <div class="weather-main">
 <div class="temperature">
 <img id="weather-icon" src="" alt="Weather icon">
 <span id="temp">--</span>°C
 </div>
 <p id="description">Weather description</p>
 </div>
 
 <div class="weather-details">
 <div class="detail">
 <span class="label">Feels Like</span>
 <span id="feels-like">--°C</span>
 </div>
 <div class="detail">
 <span class="label">Humidity</span>
 <span id="humidity">--%</span>
 </div>
 <div class="detail">
 <span class="label">Wind</span>
 <span id="wind">-- km/h</span>
 </div>
 <div class="detail">
 <span class="label">Pressure</span>
 <span id="pressure">-- hPa</span>
 </div>
 </div>
 </div>
 
 <!-- 5-Day Forecast (Bonus) -->
 <div id="forecast" class="forecast hidden">
 <h3>5-Day Forecast</h3>
 <div id="forecast-container" class="forecast-container">
 <!-- Forecast cards inserted here -->
 </div>
 </div>
 </section>
 </main>
 
 <footer>
 <p>Built with by KOOMPI Apprentice</p>
 </footer>
 </div>
 
 <script src="js/app.js"></script>
</body>
</html>
```

---

## Step 2: CSS Styling

```css
/* css/style.css */

* {
 margin: 0;
 padding: 0;
 box-sizing: border-box;
}

:root {
 --primary: #3498db;
 --primary-dark: #2980b9;
 --bg-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
 --card-bg: rgba(255, 255, 255, 0.95);
 --text: #333;
 --text-light: #666;
}

body {
 font-family: 'Segoe UI', Tahoma, sans-serif;
 background: var(--bg-gradient);
 min-height: 100vh;
 color: var(--text);
}

.container {
 max-width: 800px;
 margin: 0 auto;
 padding: 20px;
}

header {
 text-align: center;
 padding: 20px 0;
}

header h1 {
 color: white;
 font-size: 2.5rem;
 text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
}

/* Search Section */
.search-section {
 margin-bottom: 30px;
}

#search-form {
 display: flex;
 gap: 10px;
 max-width: 500px;
 margin: 0 auto;
}

#city-input {
 flex: 1;
 padding: 15px 20px;
 font-size: 1rem;
 border: none;
 border-radius: 50px;
 box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

#search-form button {
 padding: 15px 30px;
 font-size: 1rem;
 background: var(--primary);
 color: white;
 border: none;
 border-radius: 50px;
 cursor: pointer;
 transition: background 0.3s;
}

#search-form button:hover {
 background: var(--primary-dark);
}

/* Loading State */
.loading {
 text-align: center;
 padding: 50px;
 color: white;
}

.spinner {
 width: 50px;
 height: 50px;
 border: 5px solid rgba(255,255,255,0.3);
 border-top-color: white;
 border-radius: 50%;
 animation: spin 1s linear infinite;
 margin: 0 auto 20px;
}

@keyframes spin {
 to { transform: rotate(360deg); }
}

/* Error State */
.error {
 text-align: center;
 padding: 30px;
 background: var(--card-bg);
 border-radius: 20px;
 color: #e74c3c;
}

#retry-btn {
 margin-top: 15px;
 padding: 10px 25px;
 background: #e74c3c;
 color: white;
 border: none;
 border-radius: 25px;
 cursor: pointer;
}

/* Weather Display */
.weather-display {
 background: var(--card-bg);
 border-radius: 20px;
 padding: 30px;
 box-shadow: 0 10px 40px rgba(0,0,0,0.2);
}

.current-weather {
 text-align: center;
}

.weather-header h2 {
 font-size: 2rem;
 margin-bottom: 5px;
}

.weather-header p {
 color: var(--text-light);
}

.weather-main {
 padding: 30px 0;
}

.temperature {
 display: flex;
 align-items: center;
 justify-content: center;
 gap: 10px;
 font-size: 4rem;
 font-weight: bold;
}

#weather-icon {
 width: 100px;
 height: 100px;
}

#description {
 font-size: 1.5rem;
 color: var(--text-light);
 text-transform: capitalize;
 margin-top: 10px;
}

.weather-details {
 display: grid;
 grid-template-columns: repeat(2, 1fr);
 gap: 20px;
 margin-top: 30px;
 padding-top: 30px;
 border-top: 1px solid #eee;
}

@media (min-width: 500px) {
 .weather-details {
 grid-template-columns: repeat(4, 1fr);
 }
}

.detail {
 text-align: center;
}

.detail .label {
 display: block;
 font-size: 0.9rem;
 color: var(--text-light);
 margin-bottom: 5px;
}

.detail span:not(.label) {
 font-size: 1.2rem;
 font-weight: bold;
}

/* Forecast */
.forecast {
 margin-top: 30px;
 padding-top: 30px;
 border-top: 1px solid #eee;
}

.forecast h3 {
 margin-bottom: 20px;
}

.forecast-container {
 display: grid;
 grid-template-columns: repeat(5, 1fr);
 gap: 10px;
}

.forecast-card {
 background: #f8f9fa;
 border-radius: 10px;
 padding: 15px 10px;
 text-align: center;
}

.forecast-card .day {
 font-weight: bold;
 margin-bottom: 10px;
}

.forecast-card img {
 width: 50px;
 height: 50px;
}

.forecast-card .temp {
 font-weight: bold;
}

/* Utilities */
.hidden {
 display: none !important;
}

/* Footer */
footer {
 text-align: center;
 padding: 30px;
 color: rgba(255,255,255,0.8);
}

/* Responsive */
@media (max-width: 600px) {
 header h1 {
 font-size: 1.8rem;
 }
 
 .temperature {
 font-size: 3rem;
 }
 
 .forecast-container {
 grid-template-columns: repeat(3, 1fr);
 }
}
```

---

## Step 3: JavaScript Logic

```javascript
// js/app.js

// Configuration
const API_KEY = 'YOUR_API_KEY_HERE'; // Replace with your key
const API_BASE = 'https://api.openweathermap.org/data/2.5';

// DOM Elements
const searchForm = document.getElementById('search-form');
const cityInput = document.getElementById('city-input');
const loadingEl = document.getElementById('loading');
const errorEl = document.getElementById('error');
const errorMessage = document.getElementById('error-message');
const retryBtn = document.getElementById('retry-btn');
const weatherDisplay = document.getElementById('weather-display');

// State
let lastSearchedCity = '';

// Event Listeners
searchForm.addEventListener('submit', handleSearch);
retryBtn.addEventListener('click', () => searchCity(lastSearchedCity));

// Functions
async function handleSearch(e) {
 e.preventDefault();
 const city = cityInput.value.trim();
 
 if (!city) {
 showError('Please enter a city name');
 return;
 }
 
 await searchCity(city);
}

async function searchCity(city) {
 lastSearchedCity = city;
 showLoading();
 
 try {
 const weatherData = await fetchWeather(city);
 displayWeather(weatherData);
 
 // Optional: Fetch forecast
 // const forecastData = await fetchForecast(city);
 // displayForecast(forecastData);
 
 showWeather();
 } catch (error) {
 showError(getErrorMessage(error));
 }
}

async function fetchWeather(city) {
 const url = `${API_BASE}/weather?q=${encodeURIComponent(city)}&appid=${API_KEY}&units=metric`;
 
 const response = await fetch(url);
 
 if (!response.ok) {
 const error = await response.json();
 throw new Error(error.message || 'Failed to fetch weather');
 }
 
 return response.json();
}

async function fetchForecast(city) {
 const url = `${API_BASE}/forecast?q=${encodeURIComponent(city)}&appid=${API_KEY}&units=metric`;
 
 const response = await fetch(url);
 
 if (!response.ok) {
 throw new Error('Failed to fetch forecast');
 }
 
 return response.json();
}

function displayWeather(data) {
 // City and Date
 document.getElementById('city-name').textContent = 
 `${data.name}, ${data.sys.country}`;
 document.getElementById('date').textContent = 
 formatDate(new Date());
 
 // Weather Icon
 const iconCode = data.weather[0].icon;
 document.getElementById('weather-icon').src = 
 `https://openweathermap.org/img/wn/${iconCode}@2x.png`;
 document.getElementById('weather-icon').alt = 
 data.weather[0].description;
 
 // Temperature and Description
 document.getElementById('temp').textContent = 
 Math.round(data.main.temp);
 document.getElementById('description').textContent = 
 data.weather[0].description;
 
 // Details
 document.getElementById('feels-like').textContent = 
 `${Math.round(data.main.feels_like)}°C`;
 document.getElementById('humidity').textContent = 
 `${data.main.humidity}%`;
 document.getElementById('wind').textContent = 
 `${Math.round(data.wind.speed * 3.6)} km/h`;
 document.getElementById('pressure').textContent = 
 `${data.main.pressure} hPa`;
}

function displayForecast(data) {
 const container = document.getElementById('forecast-container');
 container.innerHTML = '';
 
 // Get one forecast per day (every 8th item = 24 hours)
 const dailyForecasts = data.list.filter((_, index) => index % 8 === 0).slice(0, 5);
 
 dailyForecasts.forEach(forecast => {
 const card = createForecastCard(forecast);
 container.appendChild(card);
 });
 
 document.getElementById('forecast').classList.remove('hidden');
}

function createForecastCard(forecast) {
 const card = document.createElement('div');
 card.className = 'forecast-card';
 
 const date = new Date(forecast.dt * 1000);
 const dayName = date.toLocaleDateString('en', { weekday: 'short' });
 const iconCode = forecast.weather[0].icon;
 const temp = Math.round(forecast.main.temp);
 
 card.innerHTML = `
 <div class="day">${dayName}</div>
 <img src="https://openweathermap.org/img/wn/${iconCode}.png" alt="${forecast.weather[0].description}">
 <div class="temp">${temp}°C</div>
 `;
 
 return card;
}

// UI State Functions
function showLoading() {
 loadingEl.classList.remove('hidden');
 errorEl.classList.add('hidden');
 weatherDisplay.classList.add('hidden');
}

function showError(message) {
 loadingEl.classList.add('hidden');
 errorEl.classList.remove('hidden');
 weatherDisplay.classList.add('hidden');
 errorMessage.textContent = message;
}

function showWeather() {
 loadingEl.classList.add('hidden');
 errorEl.classList.add('hidden');
 weatherDisplay.classList.remove('hidden');
}

// Helper Functions
function formatDate(date) {
 return date.toLocaleDateString('en', {
 weekday: 'long',
 year: 'numeric',
 month: 'long',
 day: 'numeric'
 });
}

function getErrorMessage(error) {
 if (error.message.includes('city not found')) {
 return 'City not found. Please check the spelling and try again.';
 }
 if (error.message.includes('401')) {
 return 'API key error. Please check your configuration.';
 }
 if (!navigator.onLine) {
 return 'No internet connection. Please check your network.';
 }
 return 'Something went wrong. Please try again.';
}

// Optional: Get user's location on load
async function getLocationWeather() {
 if ('geolocation' in navigator) {
 try {
 const position = await new Promise((resolve, reject) => {
 navigator.geolocation.getCurrentPosition(resolve, reject);
 });
 
 const { latitude, longitude } = position.coords;
 const url = `${API_BASE}/weather?lat=${latitude}&lon=${longitude}&appid=${API_KEY}&units=metric`;
 
 const response = await fetch(url);
 const data = await response.json();
 
 displayWeather(data);
 showWeather();
 } catch (error) {
 console.log('Location access denied or failed');
 }
 }
}

// Uncomment to enable auto-location:
// getLocationWeather();
```

---

## Bonus Features

### Recent Searches (localStorage)

```javascript
function saveSearch(city) {
 let searches = JSON.parse(localStorage.getItem('recentSearches') || '[]');
 searches = searches.filter(s => s.toLowerCase() !== city.toLowerCase());
 searches.unshift(city);
 searches = searches.slice(0, 5); // Keep only 5
 localStorage.setItem('recentSearches', JSON.stringify(searches));
}

function loadRecentSearches() {
 return JSON.parse(localStorage.getItem('recentSearches') || '[]');
}
```

### Temperature Unit Toggle

```javascript
let isCelsius = true;

function toggleUnit() {
 isCelsius = !isCelsius;
 // Re-display weather with new unit
}

function convertTemp(celsius) {
 if (isCelsius) return celsius;
 return (celsius * 9/5) + 32; // To Fahrenheit
}
```

---

## Evaluation Criteria

| Criteria | Points |
|----------|--------|
| **API Integration** (30) | |
| Fetches weather correctly | 15 |
| Handles errors properly | 15 |
| **User Interface** (30) | |
| Clean, professional design | 15 |
| Responsive layout | 10 |
| Loading/error states | 5 |
| **Code Quality** (25) | |
| Clean JavaScript | 10 |
| Async/await usage | 10 |
| Error handling | 5 |
| **Bonus Features** (15) | |
| Forecast | 5 |
| Geolocation | 5 |
| Recent searches | 5 |

---

## Level Complete

Upon completing this project:

 **JavaScript Advanced Badge** earned 
 Ready for **Level 2.5: Git & GitHub** (if not done) 
 Ready for **Level 2.6: React Fundamentals**

---

<div align="center">

**You built a real application!** 

*APIs + Async = Powerful apps*

</div>
