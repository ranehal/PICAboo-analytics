# Pickaboo Price Tracker & Analytics Dashboard 🛒⚡

An end-to-end price tracking and historical analytics platform for **Pickaboo** (e-commerce in Bangladesh). Scrapes live product prices, tracks discount histories, detects All-Time Low (ATL) price deals, and provides a modern interactive dashboard built with Flask & Chart.js.

---

## 🌟 Key Features

- 🔍 **Dynamic Category Crawler**: Automatically discovers all Pickaboo categories and paginates through catalog items via API.
- 📉 **Price History & Trend Tracking**: Stores price snapshots, special offer pricing, discount percentages, and stock availability in SQLite.
- 🏷️ **All-Time Low (ATL) Detection**: Highlights products currently at their lowest historical recorded price.
- 🎨 **Modern Dark-Mode Dashboard**: Sleek Glassmorphism interface with Chart.js price trend visualization, real-time filtering, search, and category navigation.
- 🚀 **Zero-Configuration Launcher**: Simple Windows batch interface (`runall.bat`) for scraping, viewing dashboard, or running both concurrently.

---

## 📁 Repository Structure (Root / 0-Level)

```
.
├── dashboard.py         # Flask backend & embedded interactive single-page app
├── scraper.py           # Pickaboo API scraper for catalog & price snapshot ingestion
├── pickaboo_prices.db   # SQLite database storing categories, products, and price logs
├── requirements.txt     # Python dependencies
├── runall.bat           # Interactive launcher script for Windows
├── .gitignore           # Git ignore patterns
└── README.md            # Project documentation
```

---

## ⚡ Quick Start

### 1. Prerequisites & Installation

Ensure Python 3.8+ is installed. Clone the repository and install requirements:

```bash
git clone https://github.com/ranehal/PICAboo-analytics.git
cd PICAboo-analytics
pip install -r requirements.txt
```

### 2. Running the Application

#### Option A: Interactive Launcher (Windows)
Double-click or run `runall.bat` in your terminal:
```cmd
runall.bat
```
Select:
1. Scrape live prices
2. Scrape specific category IDs
3. Launch dashboard only (`http://localhost:5000`)
4. Scrape live prices & launch dashboard concurrently

#### Option B: Manual Execution

- **Run Scraper**:
  ```bash
  python scraper.py --delay 0.6
  ```
- **Launch Web Dashboard**:
  ```bash
  python dashboard.py
  ```
  Open `http://localhost:5000` in your web browser.

---

## 📊 Database Schema

The SQLite database (`pickaboo_prices.db`) contains three main tables:

- `categories`: `(id, name, slug, parent_id)`
- `products`: `(id, sku, name, slug, category_id, category_name, product_img, unit, unit_value)`
- `price_history`: `(id, product_id, price, special_price, discount, stock_available, scraped_at)`

---

## 🛠 Tech Stack

- **Backend**: Python 3, Flask, SQLite3, Requests
- **Frontend**: HTML5, CSS3 (Glassmorphism & Variables), JavaScript (ES6+), Chart.js (v4.4)
- **Tooling**: Git, Windows Batch Scripting

---

## 📜 License

MIT License © [ranehal](https://github.com/ranehal)
