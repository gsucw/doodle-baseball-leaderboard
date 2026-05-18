# 🏆 Google Doodle Baseball Leaderboard UI & API Wrapper

An open-source, lightweight, and responsive frontend dashboard designed to fetch and display the global, weekly, and daily high score rankings for the classic Google Doodle Baseball game. 

This project is built for developers and gaming communities who want to integrate competitive leaderboards into their web game mirrors.

## 🚀 Live Demo & Fullscreen Game
You can see this leaderboard system fully integrated and working in real-time on our live gaming site:
👉 **[Play Google Doodle Baseball & View Live Leaderboard](https://doodle-baseball.cc)**

---

## 📊 Open API Endpoints Included

This repository utilizes high-performance, real-time gaming API endpoints to fetch score data sorted by different time frames. You are free to use these endpoints for your own non-commercial fan projects:

### 1. All-Time Global Leaderboard
*   **URL:** `[https://api.pipsnythints.com/api/doodleBaseball/getLeaderBoard?type=1](https://api.pipsnythints.com/api/doodleBaseball/getLeaderBoard?type=1)`
*   **Method:** `GET`
*   **Description:** Fetches the all-time highest streaks (Home Runs) recorded since the launch.

### 2. Weekly Leaderboard
*   **URL:** `[https://api.pipsnythints.com/api/doodleBaseball/getWeeklyBoard?type=1](https://api.pipsnythints.com/api/doodleBaseball/getWeeklyBoard?type=1)`
*   **Method:** `GET`
*   **Description:** Fetches the top scoring players for the current calendar week. Resets every Sunday.

### 3. Daily Leaderboard
*   **URL:** `[https://api.pipsnythints.com/api/doodleBaseball/getDailyBoard?type=1](https://api.pipsnythints.com/api/doodleBaseball/getDailyBoard?type=1)`
*   **Method:** `GET`
*   **Description:** Fetches today's top batters. Perfect for tracking active daily tournaments.

---

## 💻 Quick Start: How to Fetch the Data (JavaScript Example)

You can easily render these leaderboards in your web app using the standard JavaScript `Fetch API`. Here is a clean, production-ready asynchronous function example:

```javascript
// Example: Fetching the Leaderboard Data
const API_URLS = {
    alltime: 'https://api.pipsnythints.com/api/doodleBaseball/getLeaderBoard?type=1',
    weekly: 'https://api.pipsnythints.com/api/doodleBaseball/getWeeklyBoard?type=1',
    daily: 'https://api.pipsnythints.com/api/doodleBaseball/getDailyBoard?type=1'
};

async function loadLeaderboard(type) {
    try {
        const response = await fetch(API_URLS[type]);
        if (!response.ok) throw new Error('Network response was not ok');
        
        const data = await response.json();
        console.log(`--- ${type.toUpperCase()} LEADERBOARD DATA ---`, data);
        
        // Your UI Rendering Logic Here (e.g., creating a <table> to show scores)
        // renderTable(data);
    } catch (error) {
        console.error('Failed to load leaderboard data:', error);
    }
}

// Load daily rankings on page load
loadLeaderboard('daily');
