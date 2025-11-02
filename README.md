# Automated E-Commerce Price Tracker
An independent project designed to automate daily price monitoring of products from the following e-commerce websites: KaBuM!, Mercado Livre. Built using Python, SQLite, and Windows Task Scheduler to eliminate manual price checking and enable data-driven purchasing decisions.

_Se preferir a versão em Português deste projeto, [clique aqui](https://github.com/luanfaraujo/price-tracker-ptbr)._

---

## Overview
This project demonstrates how web scraping and database automation can solve real-world problems. The system automatically collects product pricing data daily from the following e-commerce websites: KaBuM!, Mercado Livre, stores it in a normalized SQLite database, and maintains historical records for trend analysis.

Currently supports KaBuM! and Mercado Livre, with architecture designed to be extensible to additional retailers. The core techniques - web scraping, database design, and automation - apply broadly to competitive intelligence, market research, and price monitoring scenarios across industries.

---

## Objectives
- Automate daily collection of product prices from e-commerce websites.
- Store historical pricing data in a structured, queryable database.
- Bypass anti-bot detection systems using proper HTTP headers.
- Enable automated execution without manual intervention.
- Maintain audit logs for monitoring system health and troubleshooting.
- Provide foundation for future price analysis and multi-retailer support.

---

## Process

### 1. Web Scraping Development
- Analyzed website HTML structures (KaBuM! and Mercado Livre) to locate pricing data.
- Implemented HTTP headers to mimic browser requests and bypass bot detection.
- Used site-specific regular expressions to extract prices from JSON-embedded pricing data within HTML.
- Built error handling for failed requests and missing data patterns.

### 2. Database Design
- Created normalized schema with separate tables for products and price history.
- Implemented foreign key relationships to link historical prices to products.
- Used AUTOINCREMENT primary keys for automatic ID management.
- Applied parameterized queries to prevent SQL injection vulnerabilities.

### 3. Automation Implementation
- Configured Windows Task Scheduler for daily execution at specified times.
- Enabled "run after missed start" to handle system downtime.
- Implemented logging system to track execution success/failure.
- Added timestamp recording for each price collection event.

### 4. Code Quality & Security
- Refactored from f-string SQL queries to parameterized queries.
- Implemented comprehensive error handling with try-except blocks.
- Added logging at multiple levels (info, warning, error) for different scenarios.
- Structured code for maintainability and future enhancements.

---

## Results & Insights
- Successfully automated daily price collection from two major Brazilian e-commerce sites, eliminating ~15 minutes of manual work per day.
- Built historical database enabling price trend analysis and identification of optimal purchase timing.
- Achieved reliable execution through proper automation configuration and error recovery.
- Created scalable database foundation supporting multiple products.

---

## Tools & Skills Demonstrated
- **Web Scraping:** requests, regex pattern matching, anti-bot bypass techniques
- **Database Management:** SQLite, schema design, normalization, foreign keys, parameterized queries
- **Automation:** Windows Task Scheduler, logging, error handling, scheduled execution
- **Data Security:** SQL injection prevention, proper error handling, input validation
- **Software Engineering:** Version control readiness, code documentation, iterative improvement

---

## Supported Retailers
- **KaBuM!**: Full price tracking (original, cash, installments)
- **Mercado Livre**: Price tracking (cash and installments)

Each retailer requires:
- Custom regex patterns for price extraction
- Site-specific HTTP headers
- Unique URL structure handling

---

## Current Limitations & Future Enhancements
**Current Scope:**
- Currently supports KaBuM! and Mercado Livre
- Site-specific regex patterns required for each retailer
- Different URL formats across retailers

**Planned Improvements:**
- Expand to additional retailers
- Price drop email alerts when products reach target thresholds
- Data visualization dashboard showing price trends over time
- Cross-retailer comparison for the same product
- Export functionality to CSV/Excel for external analysis
- Migration to GitHub Actions for cloud-based execution
- Statistical analysis and price prediction features

---

## Technical Notes
**Database Schema:**
- `products` table: Stores product metadata (name, URL, retailer)
- `price_history` table: Stores all price records with timestamps and foreign key references

**Key Learning Points:**
- Understanding the difference between HTML and JavaScript-rendered content
- Importance of proper HTTP headers in web scraping
- Different websites require different parsing approaches (site-specific HTML/JSON structures)
- Database normalization principles and their practical benefits
- Parameterized queries vs. string interpolation for SQL
- Automation reliability and handling missed executions
