# 🛍️ Shopee Multi-Scraper (Playwright/CDP)

> **Last Updated:** 2025-12-15

A Python tool for scraping data from Shopee Thailand using DOM/UI interaction combined with **Playwright** and Chrome DevTools Protocol (CDP) connection for speed and efficiency.

This repository consists of two main scrapers:

1.  **Product Scraper:** Extracts all product listings from a Shop URL.
2.  **Review Scraper:** Extracts user reviews from specific Product URLs.

---

## ⚙️ Setup and Installation

### 1. Prerequisites

* Python 3.8+
* Google Chrome Browser (Required for running in Debug/CDP mode)

### 2. Install Python Libraries

Install the required libraries using pip:

```bash
pip install playwright pandas nest-asyncio openpyxl
playwright install chromium
```

### 3. Prepare Chrome Browser for CDP Mode

This script requires a connection to an active Chrome instance via Chrome DevTools Protocol (CDP) on port **9222**. You must launch Chrome in Debugging/CDP mode before running the script **(Do not close this Chrome window while the script is running).**

Choose one of the methods below to launch Chrome in the required mode:

#### 🟢 Method 1: Create a Desktop Shortcut (Recommended for Windows)

1.  Right-click on **Desktop → New → Shortcut**.
2.  In the **Type the location of the item** field, paste the following line entirely:
    ```text
    "C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=9222 --user-data-dir="C:\chrome_playwright_profile"
    ```
    *(Please verify that the path to chrome.exe is correct for your system)*.
3.  Click **Next**.
4.  Name the shortcut **`chrome-debug-mode`**.
5.  Click **Finish**.
6.  → Double-click the shortcut to open Chrome with `--remote-debugging-port=9222` enabled.

#### 🔵 Method 2: Create a .bat File (Recommended for Windows)

1.  Open **Notepad**.
2.  Paste the following content:
    ```batch
    @echo off
    "C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=9222 --user-data-dir="C:\chrome_playwright_profile"
    ```
    *(Please verify that the path to chrome.exe is correct for your system)*.
3.  Click **File → Save As…**.
4.  Name the file **`start_chrome_9222.bat`**.
5.  Change **Save as type** to **`All Files (*.*)`**.
6.  Double-click the `.bat` file to launch Chrome in Debugging mode.

---

## 🚀 Usage

Since the scripts are provided as **Jupyter Notebooks (.ipynb)**, we recommend running them in **VS Code** or **Jupyter Lab** for an interactive experience.

### 1. 📋 Product Scraper (Scrape Items)

* **File:** `shopee-multi-product-scraper.ipynb`
* **Objective:** Scrape all product listings from a Shop URL.
* **How to use:**
    1.  Open `shopee-multi-product-scraper.ipynb`.
    2.  Edit the `SHOP_URLS` variable in the first cell to include your target shop URLs.
    3.  Click **Run All** or run cell by cell.
* **Output:** Saves as an Excel file named `shopee_products_[timestamp].xlsx`.

### 2. 💬 Review Scraper (Scrape Comments)

* **File:** `shopee-reviews-scraper.ipynb`
* **Objective:** Scrape user reviews from specific Product URLs.
* **How to use:**
    1.  Open `shopee-reviews-scraper.ipynb`.
    2.  Edit the `PRODUCTS_URLS` variable to include your target product URLs.
    3.  Click **Run All** or run cell by cell.
* **Output:** Saves as an Excel file named `shopee_reviews_[timestamp].xlsx`.

---

## 🛠️ Repository File Structure

| Filename | Description |
| :--- | :--- |
| `shopee-multi-product-scraper.ipynb` | Notebook for scraping products from Shop URLs (includes Excel save function). |
| `shopee-reviews-scraper.ipynb` | Notebook for scraping reviews from Product URLs. |

---

## 📊 Data Dictionary

### 1. Product Data (`shopee_products_...xlsx`)
This file contains all product listings scraped from the shop page.

| Column Name | Description |
| :--- | :--- |
| `shop_id` | Shop ID |
| `product_id` | Product ID |
| `shop_name` | Name of the Shop |
| `product_name` | Name of the Product |
| `price` | Product Price (THB) |
| `sold` | Number of items sold |
| `rating` | Average product rating (Stars) |
| `url` | Link to the product page |
| `collected_at` | Timestamp of data collection |

### 2. Review Data (`shopee_reviews_...xlsx`)
This file contains customer reviews for the products.

| Column Name | Description |
| :--- | :--- |
| `shop_id` | Shop ID |
| `product_id` | Product ID |
| `shop_name` | Name of the Shop |
| `product_name` | Name of the Product |
| `user` | Reviewer's username (Masked) |
| `rating` | Rating given by the customer (1-5 Stars) |
| `date` | Date and time of the review |
| `option` | Product variant purchased (e.g., Color, Size) |
| `comment` | Review text |
| `collected_at` | Timestamp of data collection |
