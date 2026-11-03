# FinTrack

A finance analytics dashboard that turns raw KPIs, products and transactions into clear charts, tables and a revenue forecast.

**Live demo:** https://fintrack-finance.netlify.app/

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-764ABC?style=flat-square&logo=redux&logoColor=white)
![MUI](https://img.shields.io/badge/MUI-007FFF?style=flat-square&logo=mui&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)

## Features

**Dashboard** (10 panels in a responsive grid)
- Revenue and expenses, profit and revenue, and month-by-month revenue trends
- Operational vs non-operational expenses
- Campaign targets and expense breakdown by category (pie charts)
- Product prices vs expenses (scatter plot)
- Product list and recent orders (sortable data grids)

**Predictions**
- Revenue forecast for the next year using **linear regression** on monthly revenue, with the regression line and predicted values plotted against actuals

**Engineering**
- **RTK Query** for API calls with built-in caching
- Fully typed frontend in **TypeScript**, with a custom MUI theme
- Charts built with **Recharts** (area, line, bar, pie and scatter)
- REST API on Express with Mongoose models for KPIs, products and transactions, plus security headers via Helmet

## Architecture

```
React + TypeScript (Vite)  ──RTK Query──►  Express REST API  ──►  MongoDB
```

| Endpoint | Returns |
|---|---|
| `GET /kpi/kpis` | Revenue, expenses and profit by month and day, expenses by category |
| `GET /product/products` | Products with price and expense |
| `GET /transaction/transactions` | Recent transactions |

## Running Locally

**Backend**:
```bash
cd server
npm install
npm run dev
```
Create `server/.env`:
```
MONGO_URL=your_mongodb_connection_string
PORT=9000
```
To load the sample data the first time, uncomment the `insertMany` lines in `server/index.js`, run once, then comment them again.

**Frontend**:
```bash
cd client
npm install
npm run dev
```
Create `client/.env`:
```
VITE_BASE_URL=http://localhost:9000
```

## Project Structure

```
FinTrack/
├── client/
│   └── src/
│       ├── scenes/dashboard/     # Dashboard rows and chart panels
│       ├── scenes/predictions/   # Revenue forecasting page
│       ├── state/                # RTK Query API and types
│       └── components/           # Shared layout components
└── server/
    ├── models/                   # KPI, Product, Transaction
    ├── routes/                   # REST endpoints
    └── data/                     # Sample seed data
```

## Author

**Ritu Sharma** · [GitHub](https://github.com/Ritu84) · [LinkedIn](https://www.linkedin.com/in/ritu-sharma-a2580222a/)
