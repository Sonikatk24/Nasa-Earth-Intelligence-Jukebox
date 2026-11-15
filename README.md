# NASA Earth Intelligence Jukebox

**Discover Earth. Predict Changes. Protect Our Future.**
Team **TechHackers** · NASA Space Apps Challenge 2026 · *The Earth Information Jukebox*

An interactive web app that lets people **see, hear and explore** NASA Earth data. It turns NASA satellite imagery into live sound, compares places and years, and explains climate records in plain language.

> Not an official NASA product. The Earth Health Score and Future Earth simulator are our own illustrative indicators, not NASA measurements or climate predictions.

## Features
- **Earth Jukebox:** NASA GIBS imagery is analysed in the browser and played as live generated sound (Web Audio API). Colour sets the chord, brightness sets loudness and pitch, saturation shapes the tone, bright-pixel density sets rhythm. Each frame gets a text description for screen-reader users.
- **Explore Earth:** location search, NASA GIBS satellite map, NASA POWER charts (temperature, rainfall, humidity) for 1, 5 or 10 years.
- **Ask Earth AI:** rule-based answers built from retrieved NASA data, with the source named (no trained AI model or LLM).
- **Future Earth:** what-if simulator (temperature, rainfall, vegetation). Illustrative only.
- **Time Machine:** compare satellite imagery from two years, timelapse, and a table of climate change between them.
- **Danger Alerts:** temperature and rainfall anomalies from NASA POWER; fire detections from NASA FIRMS when a key is set.
- **Earth Health Score:** transparent custom 0-100 indicator with its method and limits shown.
- **Mission Mode:** data missions checked per location, with points saved in SQLite.

## Tech stack
React + Vite, Tailwind CSS, React Router, Leaflet / React-Leaflet, Recharts, Lucide icons · Python Flask, Pandas, NumPy, Requests · SQLite · Web Audio API.

## NASA data sources
- [NASA POWER](https://power.larc.nasa.gov/docs/) monthly point API (T2M, PRECTOTCORR, RH2M)
- [NASA GIBS](https://nasa-gibs.github.io/gibs-api-docs/) satellite imagery tiles
- [NASA FIRMS](https://firms.modaps.eosdis.nasa.gov/) active fire detections (optional MAP_KEY)
- Place search: OpenStreetMap Nominatim

## Run locally
**Backend**
```bash
cd backend
pip install -r requirements.txt
# optional, for live fire data (free key: https://firms.modaps.eosdis.nasa.gov/api/map_key/)
# PowerShell: $env:FIRMS_MAP_KEY="your_key"      bash: export FIRMS_MAP_KEY=your_key
python app.py
```
**Frontend** (new terminal)
```bash
cd frontend
npm install
npm run dev
```
Open http://localhost:5173. The frontend proxies `/api` to Flask on port 5000. An internet connection is required for NASA data.

## Limitations
Fire data needs a FIRMS key. Imagery coverage varies by place and date. The health score uses humidity as a proxy for vegetation. The simulator uses simple linear rules, not a climate model. The sound mapping is artistic, not a calibrated measurement.
