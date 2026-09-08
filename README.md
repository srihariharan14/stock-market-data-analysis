# 📈 Stock Data Extraction & Visualization

A Python-based data analysis project that extracts historical stock prices and quarterly revenue data for **Tesla (TSLA)** and **GameStop (GME)**, then visualizes the two datasets together using interactive Plotly charts.

The project demonstrates how financial data can be collected from APIs and web pages, cleaned into usable DataFrames, and transformed into visualizations that make it easier to explore relationships between a company's stock performance and revenue.

## 📌 Project Overview

Financial analysis often requires combining data from multiple sources. In this project:

* Historical stock-price data is obtained using the `yfinance` library.
* Quarterly revenue data is extracted through web scraping.
* `BeautifulSoup` is used to parse HTML tables.
* Pandas DataFrames are used to organize the extracted information.
* Plotly is used to create interactive visualizations.
* Stock price and revenue are displayed together over time.

The notebook focuses on two companies:

* **Tesla (TSLA)**
* **GameStop (GME)**

The project follows six main tasks covering data extraction, web scraping, and visualization.

## 🎯 Objectives

The main objectives are to:

1. Retrieve historical stock-market data programmatically.
2. Extract quarterly company revenue from web-based tables.
3. Convert raw information into structured Pandas DataFrames.
4. Process dates and financial values for visualization.
5. Build reusable plotting functionality.
6. Compare historical stock prices with historical revenue.

## 🛠️ Technologies Used

* **Python**
* **Pandas** — data manipulation and DataFrames
* **yfinance** — historical stock-market data
* **Requests** — HTTP requests for web scraping
* **BeautifulSoup** — HTML parsing
* **Plotly** — interactive data visualization

The notebook imports `yfinance`, `pandas`, `requests`, BeautifulSoup, and Plotly for these tasks.

## 📊 Data Sources

### Stock Data

Historical stock information is retrieved using `yfinance`.

For Tesla, a `Ticker` object is created using the `TSLA` ticker symbol, and historical data is requested using:

```python
tesla_ticker = yf.Ticker("TSLA")

tesla_data = tesla_ticker.history(period="max")
```

The resulting dataset contains fields including:

* Date
* Open
* High
* Low
* Close
* Volume
* Dividends
* Stock Splits

The same approach is used for GameStop using its ticker symbol.

### Revenue Data

Quarterly revenue data is obtained through web scraping.

The project uses `requests` to retrieve the webpage and `BeautifulSoup` to parse its HTML structure. The relevant revenue table is then extracted and converted into a DataFrame containing:

```text
Date
Revenue
```

For example, the Tesla revenue dataset includes quarterly observations such as:

| Date       |  Revenue |
| ---------- | -------: |
| 2022-09-30 | $21,454M |
| 2022-06-30 | $16,934M |
| 2022-03-31 | $18,756M |
| 2021-12-31 | $17,719M |

The source data extends back through earlier Tesla quarters.

## 🔄 Data Extraction Workflow

The project follows this general pipeline:

```text
Financial Data Sources
        │
        ├───────────────┐
        │               │
        ▼               ▼
   yfinance        Web Scraping
        │               │
        ▼               ▼
 Stock Prices       Revenue Data
        │               │
        └───────┬───────┘
                ▼
        Pandas DataFrames
                │
                ▼
        Data Preparation
                │
                ▼
      Interactive Plotly Graph
```

## 📈 Visualization

A reusable `make_graph()` function is defined to combine stock-price and revenue data into a two-panel Plotly visualization.

The function accepts:

```python
make_graph(stock_data, revenue_data, stock)
```

and generates:

1. **Historical Share Price**
2. **Historical Revenue**

Both plots share the same date axis, allowing the two time series to be examined together.

The visualization uses:

* Date on the x-axis
* Share price in US dollars on the first y-axis
* Revenue in US millions on the second y-axis
* An interactive Plotly range slider

## 🚗 Tesla Analysis

Tesla's historical stock data is extracted using the `TSLA` ticker, with the maximum available historical period requested.

Tesla's quarterly revenue is then scraped from the provided HTML source and structured into a DataFrame.

The final visualization combines Tesla's historical share price and revenue into a single interactive figure.

## 🎮 GameStop Analysis

The same workflow is applied to GameStop:

1. Retrieve historical GME stock data using `yfinance`.
2. Extract GameStop quarterly revenue using web scraping.
3. Structure the revenue information in a Pandas DataFrame.
4. Visualize stock price and revenue together using the reusable plotting function.

This makes it possible to apply the same analysis pipeline to multiple companies.

## 📁 Project Structure

```text
stock-data-analysis/
│
├── Extracting and Visualizing Stock Data.ipynb
└── README.md
```

## ▶️ Running the Project

### Install Dependencies

```bash
pip install yfinance pandas requests beautifulsoup4 plotly
```

### Run the Notebook

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Extracting and Visualizing Stock Data.ipynb
```

Alternatively, the notebook can be run in Google Colab.

## 🔑 Key Concepts Demonstrated

### API-Based Data Extraction

Using `yfinance` to retrieve historical market data programmatically.

### Web Scraping

Using `requests` and `BeautifulSoup` to retrieve and parse HTML-based financial information.

### Data Manipulation

Using Pandas to transform extracted information into structured DataFrames.

### Data Visualization

Using Plotly to create interactive charts that combine multiple financial indicators.

### Reusable Functions

The `make_graph()` function encapsulates the visualization logic so that the same process can be applied to different companies.

## 💡 What This Project Shows

This project demonstrates a basic but practical financial-data workflow:

> **Extract → Clean → Structure → Visualize**

Rather than relying on a pre-existing CSV file, the project demonstrates how data can be collected programmatically from different sources and combined into a meaningful visualization.

## 🚀 Possible Improvements

The project could be extended by:

* Adding additional companies for comparison
* Calculating stock returns and volatility
* Adding moving averages
* Comparing revenue growth with stock-price growth
* Calculating year-over-year revenue changes
* Adding trading volume analysis
* Building correlation analysis between financial metrics
* Automating data collection on a scheduled basis
* Creating a financial dashboard using Streamlit or Dash
* Using more robust data-validation and cleaning pipelines
* Replacing static historical sources with current financial-data APIs

## 👤 Author

**Srihari Haran**

GitHub: [srihariharan14](https://github.com/srihariharan14)

---

⭐ If you found this project useful, consider giving the repository a star!
