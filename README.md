# GEO_TESTAPI

A simple Node.js + Express web app that calculates travel time from the user’s current location to a fixed destination using the Google Maps Distance Matrix service. The app also registers a service worker and requests notification permission.

## What the app does

- Serves a static frontend from an Express server (`server.js`)
- Gets the user’s current geolocation in the browser
- Calls Google Maps Distance Matrix to estimate driving duration
- Displays the travel time in `HH:MM:SS` format
- Registers a service worker (`sw.js`)
- Requests notification permission and attempts push subscription
- Triggers a sample notification every minute from the service worker

## Tech stack

- Node.js 18
- Express 4
- Vanilla HTML/CSS/JavaScript
- Google Maps JavaScript API (Distance Matrix)
- Service Worker + Web Notifications

## Project structure

- `/server.js` — Express server (serves static files on port `3000`)
- `/index.html` — Main page and inline app logic
- `/index.js` — Distance/geo logic (similar logic also embedded in `index.html`)
- `/sw.js` — Service worker, fetch handling, push subscription, notifications
- `/style.css` — Basic page styling
- `/vercel.json` — Vercel routing config

## Requirements

- Node.js `18.x`
- A browser that supports:
  - Geolocation API
  - Service Workers
  - Notifications

## Setup and run

1. Install dependencies:

```bash
npm install
```

2. Start the server:

```bash
npm start
```

3. Open in browser:

- `http://localhost:3000`

4. Allow permissions when prompted:

- Location access
- Notification access

## Configuration notes

- A Google Maps API key is currently hardcoded in `index.html` (`apiKey` variable).
- A VAPID public key is currently hardcoded in `sw.js` (`public_key` variable).

For production use, move these values to secure configuration and avoid committing sensitive keys to source control.

## Current scripts

From `package.json`:

- `npm start` — runs `node server.js`
- `npm test` — placeholder script that currently exits with an error

## Known limitations

- The destination is fixed in code (UIT coordinates) and not user-configurable.
- `index.html` duplicates most of the logic from `index.js`.
- No automated test suite is currently implemented.
- Service worker fetch handler does not implement an explicit cache population strategy.
