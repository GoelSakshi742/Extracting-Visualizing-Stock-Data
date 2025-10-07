<p align="center">
  <a href="https://skills.network/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkPY0220ENSkillsNetwork900-2022-01-01" target="_blank">
    <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/assets/logos/SN_web_lightmode.png" width="200" alt="Skills Network Logo">
  </a>
</p>

# 🚀 Extracting and Visualizing Stock Data 📈

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![YFinance](https://img.shields.io/badge/yfinance-FF9900?style=for-the-badge)
![Plotly](https://img.shields.io/badge/plotly-3F4F60?style=for-the-badge)
![Web Scraping](https://img.shields.io/badge/BeautifulSoup-4B0082?style=for-the-badge)

---

## 🔍 Project Overview

This project focuses on extracting and visualizing **stock price** and **revenue data** for two major companies, **Tesla** and **GameStop**. Using the `yfinance` Python library, historical stock data is retrieved programmatically. Additionally, revenue data is scraped from the web using `requests` and `BeautifulSoup`. Both datasets are cleaned and processed, then visualized with interactive Plotly graphs that show trends and historical data up to mid-2021.

---

## 🎨 Core Features

- **Stock Data Extraction:** Uses `yfinance.Ticker` API to fetch maximum available historical stock prices.
- **Web Scraping Revenue:** Uses `requests` and `BeautifulSoup` to pull quarterly revenue data from publicly available webpages.
- **Data Cleaning:** Handles date parsing, removal of currency symbols, and missing data.
- **Interactive Visualization:** The `make_graph` function generates dual-subplot interactive charts combining stock prices and revenue over time.
- **Data Restriction:** Graphs focus on data leading up to June 2021 for actionable visualization.

---

## 🔧 Setup & Libraries

Run these commands to install required libraries if working locally:

pip install yfinance bs4 nbformat --upgrade plotly

text

Key libraries used:

- `yfinance` for stock extraction  
- `BeautifulSoup` & `requests` for scraping  
- `plotly` for interactive charts  
- `pandas` for data manipulation

---

## 📊 Visualization Function — `make_graph`

import datetime
from plotly.subplots import make_subplots
import plotly.graph_objects as go

def make_graph(stock_data, revenue_data, stock):
fig = make_subplots(
rows=2, cols=1, shared_xaxes=True,
subplot_titles=("Historical Share Price", "Historical Revenue"),
vertical_spacing=0.3)

text
cutoff_date = datetime.date(2021, 6, 14)
stock_data_specific = stock_data[stock_data.Date <= cutoff_date]

cutoff_revenue_date = datetime.date(2021, 4, 30)
revenue_data_specific = revenue_data[revenue_data.Date <= cutoff_revenue_date]

fig.add_trace(go.Scatter(
    x=pd.to_datetime(stock_data_specific.Date),
    y=stock_data_specific.Close.astype("float"),
    name="Share Price"), row=1, col=1)

fig.add_trace(go.Scatter(
    x=pd.to_datetime(revenue_data_specific.Date),
    y=revenue_data_specific.Revenue.astype("float"),
    name="Revenue"), row=2, col=1)

fig.update_xaxes(title_text="Date", row=1, col=1)
fig.update_xaxes(title_text="Date", row=2, col=1)
fig.update_yaxes(title_text="Price ($US)", row=1, col=1)
fig.update_yaxes(title_text="Revenue ($US Millions)", row=2, col=1)

fig.update_layout(showlegend=False,
                  height=900,
                  title=stock,
                  xaxis_rangeslider_visible=True)
fig.show()
text

Use this function to visualize Tesla and GameStop stock and revenue data effectively.

---

## 📂 Other Files in the Repository

### 1. `EnumerateLoop.py` 🌀

- Demonstrates Python's `enumerate()` in loops, enabling index-value access during iteration.  
- Includes a simple function `add(a)` that increments input by one.  
- Prints outputs to illustrate basic Python control flow and function usage.

for i, x in enumerate(['A', 'B', 'C']):
print(i, x)

def add(a):
return a + 1

print(add(4))

text

---

### 2. `High order functions.ipynb` 🧮

- A Jupyter notebook showcasing anonymous functions via **lambda expressions**.  
- Illustrates concise function definitions for small one-line operations.  
- Demonstrates using lambdas in Python for functional programming style (e.g., mapping, filtering).

---

### 3. `htmlparsing.py` 🌐

- A Python script performing basic web scraping example:  
  - Uses `urllib.request.urlopen` to fetch HTML from a URL.  
  - Parses the HTML content with `BeautifulSoup`.  
  - Extracts and prints all text from the webpage.

Example URL: `http://olympus.realpython.org/profiles/dionysus`

from bs4 import BeautifulSoup
from urllib.request import urlopen

url = "http://olympus.realpython.org/profiles/dionysus"
page = urlopen(url)
html = page.read().decode("utf-8")
soup = BeautifulSoup(html, "html.parser")
print(soup.get_text())

text

---

<p align="center">
  <strong>© 2025 Project Repository - All rights reserved</strong>
</p>

<p align="center">
  <a href="https://github.com/GoelSakshi742/Extracting-Visualizing-Stock-Data.git" target="_blank">
    <img src="https://img.shields.io/badge/GitHub-Repository-black?style=for-the-badge&logo=github" alt="GitHub Repo">
  </a>
</p>
