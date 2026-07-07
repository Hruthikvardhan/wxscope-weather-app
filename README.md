# WXSCOPE — Weather Intelligence Terminal

> Real-time atmospheric intelligence system built with pure vanilla JavaScript

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat&logo=vercel&logoColor=white)

---

## 🔗 Live Demo

**[https://wxscope-weather-app.vercel.app](https://wxscope-weather-app.vercel.app)**

---

## 📌 About The Project

WXSCOPE is a real-time weather application that looks and feels like a radar operations terminal.
Built from scratch using only HTML, CSS, and Vanilla JavaScript — zero frameworks, zero libraries.

The entire UI accent color dynamically changes based on the current weather condition.
Sunny cities show amber, rainy cities shift to blue, storms turn orange — all driven by a single CSS variable.

---

## ✨ Features

- 🔍 **City Search** — search weather for any city in the world
- 📍 **Auto GPS Detection** — detects your location automatically on page load
- 🌡 **Temperature Toggle** — switch between Celsius and Fahrenheit without re-fetching
- 📅 **5-Day Forecast** — grouped daily forecast with high and low temperatures
- 🎨 **Dynamic Color Themes** — entire UI recolors based on weather condition
- 🕐 **Search History** — recent searches saved in localStorage, persist after refresh
- ⚡ **Parallel API Calls** — current weather and forecast fetched simultaneously using Promise.all
- 🔄 **Animated SVG Gauges** — humidity, wind speed, feels like, visibility
- 📱 **Fully Responsive** — mobile, tablet, and desktop layouts
- ⚠️ **Error Handling** — handles all API errors (401, 404, 429, 500) and GPS errors

---

## 🛠 Tech Stack

| Technology | Usage |
|---|---|
| HTML5 | Semantic page structure |
| CSS3 | Styling, animations, CSS variables, responsive layout |
| Vanilla JavaScript | All logic, API calls, DOM manipulation |
| OpenWeather API | Live weather data and 5-day forecast |
| Geolocation API | Auto detect user location |
| localStorage | Persist search history across sessions |
| Vercel | Deployment and hosting |
| GitHub | Version control |

---

## 📐 Architecture & Key Concepts

**Parallel API Fetching**
```js
const [wxRes, fcRes] = await Promise.all([
    fetch(`/weather?q=${city}&appid=${API_KEY}`),
    fetch(`/forecast?q=${city}&appid=${API_KEY}`)
]);
```
Both endpoints fetched simultaneously — cuts load time in half compared to sequential awaits.

**Dynamic Theming via CSS Variables**
```css
body.wx-rain { --wx-accent: #4d9fff; }
body.wx-sunny { --wx-accent: #f5a623; }
```
One CSS variable controls 50+ UI elements. JS adds a class to body — entire dashboard recolors instantly.

**SVG Arc Gauge Animation**
```js
const offset = CIRCUMFERENCE * (1 - value / max);
arcElement.style.strokeDashoffset = offset;
```
Gauges animate from 0 to value using stroke-dashoffset transition on every new city search.

---

## 🚀 Setup & Installation

```bash
# 1. Clone the repository
git clone https://github.com/Hruthikvardhan/wxscope-weather-app.git

# 2. Open the project folder
cd wxscope-weather-app

# 3. Add your OpenWeather API key in script.js
const API_KEY = 'your_api_key_here';

# 4. Open index.html in browser
```

Get a free API key at [openweathermap.org](https://openweathermap.org/api)

> Note: New API keys take 10-15 minutes to activate after signup.

---

## 📁 Project Structure

```
wxscope-weather-app/
├── index.html                    # HTML structure
├── style.css                     # All styles and animations
├── script.js                     # All JavaScript logic
├── README.md                     # Project documentation
├── 1_requirement_gathering.txt   # Project requirements
├── 2_paper_design.txt            # Design decisions
├── 3_sprint_plan.txt             # Agile sprint breakdown
├── 4_manual_testing.txt          # Test cases
└── 5_vercel_deployment.txt       # Deployment steps
```

---

## 🧪 API Endpoints Used

```
Current Weather  →  /data/2.5/weather?q={city}&units=metric
5-Day Forecast   →  /data/2.5/forecast?q={city}&units=metric
By GPS Coords    →  /data/2.5/weather?lat={lat}&lon={lon}&units=metric
```

---

## 📱 Responsive Breakpoints

| Screen | Layout |
|---|---|
| Mobile 375px | Single column, 2x2 gauge grid |
| Tablet 768px | Single column, 2x2 gauge grid |
| Desktop 1024px+ | Two column main grid, 4x1 gauge row |

---

## 🗂 Development Methodology

Built using **Agile methodology** with 3 one-week sprints.

- **Sprint 1** — Core foundation: search, API fetch, basic display
- **Sprint 2** — Features: forecast, GPS, unit toggle, history, gauges
- **Sprint 3** — Polish: animations, responsive, testing, deployment

Task tracking done manually using sprint planning document.

---

## 👨‍💻 Author

**Hruthik Vardhan**
- GitHub: [@Hruthikvardhan](https://github.com/Hruthikvardhan)
- Live Project: [wxscope-weather-app.vercel.app](https://wxscope-weather-app.vercel.app)

---

## 📄 License

This project is licensed under the MIT License.
