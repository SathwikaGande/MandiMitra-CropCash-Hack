# Project Report — MandiMitra: CropCash Hack

## 1. Project overview
MandiMitra is a smart agricultural market-intelligence dashboard prototype. It is designed to help a farmer compare indicative crop prices across sample APMC mandis, understand recent price movement, estimate transport-adjusted proceeds and create price-threshold alerts.

## 2. Problem statement
Farmers may need to compare market rates and transport costs before choosing where and when to sell. A single modal price does not show the full picture because distance, vehicle cost, market deductions, crop shelf life and arrivals can affect the farmer's realized proceeds.

## 3. Objectives
- Present crop and mandi rate information in one dashboard.
- Show historical modal-price and arrival trends with a 7-day EMA line.
- Provide a rule-based sell/hold/transport suggestion.
- Estimate perishability risk using harvest age and humidity inputs.
- Compare net proceeds after estimated transport and market cess.
- Let users configure price alerts and share a rate digest.
- Support English, Hindi, Telugu and Marathi UI labels.
- Retain demo data and alerts in browser LocalStorage.

## 4. Main modules
1. **Dashboard KPIs:** selected crop, mandi, modal price, min/max range, arrivals and indicative forecast.
2. **Sell-timing advisor:** heuristic decision tree based on EMA momentum, arrivals, nearby market comparison and perishability score.
3. **Perishability estimator:** estimates a 0–100 risk score from days since harvest and humidity.
4. **Price trend chart:** Chart.js visualization of modal price, EMA-7 and arrivals for 30/60/90 days.
5. **Mandi explorer:** search and filter crop/mandi cards.
6. **Net profit calculator:** gross revenue minus estimated transport and cess.
7. **Price alerts:** save and remove crop price thresholds.
8. **WhatsApp digest:** formats selected crop's sample mandi rates for sharing.
9. **Language selector and offline cache:** translated key labels and browser-side persistence.

## 5. Technology stack
- HTML5 for page structure
- CSS3 and Tailwind CSS CDN for styling
- Vanilla JavaScript for state, calculations and interactions
- Chart.js for trend visualization
- Lucide for icons
- LocalStorage for client-side caching
- Node.js built-in HTTP server for optional local hosting and demo API endpoints

## 6. Data and calculation approach
The current source generates a deterministic 90-day sample dataset for five crop categories and six mandi locations. EMA-7 uses smoothing factor `2 / (7 + 1)`. Net proceeds are estimated as:

`Net proceeds = (Modal price × Quantity) − Transport cost − Market cess`

The transport estimate uses the selected vehicle rate, mandi distance and a 1.4 multiplier. The perishability estimate combines harvest-age ratio and a humidity penalty.

## 7. Limitations
- The current prices and arrivals are seeded/simulated values, not a live APMC feed.
- The forecast and sell/hold/transport rules are heuristics and are not validated agricultural or financial predictions.
- Transport, cess and hamali costs vary by route, vehicle, market and negotiation; calculator values are estimates.
- Browser LocalStorage is device/browser-specific and is not a cloud database.
- CDN libraries require internet access unless locally bundled.

## 8. Future scope
- Integrate a verified APMC/data.gov.in market-price API.
- Add a secure database and farmer accounts.
- Add location-aware route distances and verified transport quotes.
- Validate recommendation logic with agronomists and historical market data.
- Add accessibility testing and more complete translations.
- Add automated tests for calculations and API integration.

## 9. How to run
From the project root, run `npm start` and open `http://localhost:3000`. Alternatively, open `frontend/index.html` directly in a modern browser. Full setup steps are in the root README.

## 10. Conclusion
MandiMitra demonstrates how market comparison, trend visualization, spoilage awareness and transport-adjusted net-proceeds estimation can be combined in a farmer-oriented interface. The current deliverable is a demo prototype; live market data and validated decision support are recommended next steps before real-world use.
