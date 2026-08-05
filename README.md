# 🛒 Pickaboo Price Tracker & Analytics Dashboard

> **Gadget & Electronics Price History Tracking, Discount Telemetry & All-Time Low (ATL) Detection Engine for Pickaboo.**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-0099ff?style=for-the-badge&logo=github)](https://ranehal.github.io/PICAboo-analytics/)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Framework-Flask-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![SQLite3](https://img.shields.io/badge/Database-SQLite3-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://www.sqlite.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

---

## 📌 Executive Summary

**PICAboo Analytics** is an end-to-end gadget price tracker and deal discovery platform for [Pickaboo](https://www.pickaboo.com), one of Bangladesh's leading electronics and smartphone e-commerce stores.

The platform continuously crawls Pickaboo's catalog APIs, tracks historical price snapshots, measures discount percentages, detects **All-Time Low (ATL)** price drops, and visualizes price trends via a modern Flask-powered Glassmorphism dark-mode dashboard.

---

## 🚀 Key Features

- **🔍 Automated Category Crawler**: Recursively discovers categories and paginates through Pickaboo product catalogs.
- **🏷️ All-Time Low (ATL) Detection**: Highlights products currently sitting at their lowest historical recorded price.
- **📉 Price Trend Analytics (Chart.js)**: Interactive historical price modals displaying fluctuations, special offer pricing, and stock availability.
- **🎨 Glassmorphism Dark-Mode UI**: Sleek translucent dark interface with instant search, category filtering, and responsive grid layouts.
- **⚡ Batch Launcher (`runall.bat`)**: Zero-configuration Windows launcher script for automated scraping and web server execution.

---

## 🏗️ System Architecture

```mermaid
flowchart TD
    subgraph Ingestion ["⚡ Scraper Engine (scraper.py)"]
        Crawler[Pickaboo API Crawler] -->|Fetch Categories & Products| PickabooAPI[Pickaboo REST API]
        PickabooAPI -->|Ingest Price & Stock Snapshots| DB[(SQLite: pickaboo_prices.db)]
    end

    subgraph Backend ["🖥️ Flask Backend (dashboard.py)"]
        DB -->|Query Products & Price History| Flask[Flask REST API :5000]
        Flask -->|Serve Embedded Dashboard| UI[Glassmorphism Dark UI]
    end

    subgraph User_Interface ["📊 Interactive Dashboard"]
        UI -->|Render Trends| ChartJS[Chart.js Modal Graphs]
        UI -->|Filter ATL Deals| ATL[All-Time Low Indicator]
    end
```

---

## 📁 Repository Structure

```
PICAboo/
├── scraper.py           # Pickaboo catalog crawler & price snapshot ingestion script
├── dashboard.py         # Flask web server & embedded single-page interactive application
├── pickaboo_prices.db   # SQLite database storing categories, products, and price history
├── runall.bat           # Interactive Windows batch launcher
├── requirements.txt     # Python dependencies (Flask, requests)
└── README.md            # Technical documentation
```

---

## 🛠️ Database Schema (`pickaboo_prices.db`)

- **`categories`**: `(id, name, slug, parent_id)`
- **`products`**: `(id, sku, name, slug, category_id, category_name, product_img, unit, unit_value)`
- **`price_history`**: `(id, product_id, price, special_price, discount, stock_available, scraped_at)`

---

## ⚡ Quick Start & Usage

### 1. Interactive Windows Launcher
Double-click or run [`runall.bat`](file:///C:/PROJECTS/PICAboo/runall.bat):
```cmd
runall.bat
```
Select:
1. Scrape live prices across all categories.
2. Scrape specific category IDs.
3. Launch dashboard server only (`http://localhost:5000`).
4. Scrape live prices and launch dashboard concurrently.

### 2. Manual CLI Execution
```bash
# Install dependencies
pip install -r requirements.txt

# Run scraper CLI
python scraper.py --delay 0.6

# Launch Flask web dashboard
python dashboard.py
```
Open `http://localhost:5000` in your web browser.

---

## 📜 License

Distributed under the MIT License. Data rights belong to Pickaboo. Built for analytical and personal price tracking purposes.
