# Sales & Customer Analysis

This repository contains an interactive Jupyter Notebook analysis of sales and customer data and a dashboard-style set of visualizations summarised in the notebook.

## Project Overview

The analysis focuses on exploring sales performance, profitability, product performance, geographic distribution, and customer segments. The included notebook recreates a "Sales Performance Dashboard" (see image) with the following panels:

- **Total Sales**: KPI showing aggregate sales (example from dataset: ~118.73M).
- **Total Profit**: KPI showing aggregate profit (example: ~16.89M).
- **Sales by Country**: Horizontal bar chart ranking countries (example: United States, Canada, France, Germany, Mexico).
- **Sales Trend Over Time**: Time-series area/line chart showing monthly sales trends (example period: 2013–2014).
- **Sales by Product**: Column chart showing top products by sales (example products: Paseo, VTT, Velo, Amarilla, Montana, Carretera).
- **Segment Tiles**: Quick-look tiles / filters for customer segments (Channel Partners, Enterprise, Government, Midmarket, Small Business).
- **Yearly Totals**: Compact year-by-year totals (example: 2013 and 2014 values shown in the dashboard).

## Files

- `customer_data.csv` — Raw dataset used by the notebook.
- `Sales_&_Customer_Analysis.ipynb` — Jupyter Notebook that loads the CSV, performs cleaning, computes KPIs and renders visualizations.
- `README.md` — This file.

## Dataset (expected columns)

The notebook and visualizations assume a tabular dataset with columns similar to the list below. Adjust names in the notebook if your CSV uses different headers.

- `OrderID` or `TransactionID` — unique identifier per order
- `OrderDate` or `Date` — order date (parseable to datetime)
- `CustomerID` — customer identifier
- `Country` — customer country
- `Product` — product name
- `Segment` — customer segment (e.g., Enterprise, Small Business)
- `Sales` — sales amount (numeric)
- `Profit` — profit amount (numeric)
- `Year` / `Month` (optional) — derived from `OrderDate` for aggregation

Sample values visible in the dashboard image: sales totals in millions, country names like "United States of America", and product names such as "Paseo" and "VTT".

## Notebook walkthrough

The notebook is organized into logical sections:

1. **Load & Inspect Data** — read `customer_data.csv`, show head, dtypes, missing-value checks.
2. **Cleaning & Transformations** — parse dates, create `Year`/`Month` columns, coerce numeric columns, handle missing values.
3. **KPIs** — compute `total_sales`, `total_profit`, and other high-level metrics.
4. **Visualizations** — generate the dashboard elements: sales-by-country bar chart, product sales bar chart, time-series of sales, and segment tiles.
5. **Filtering & Interactivity** — notebook contains example code using `ipywidgets` or Plotly to filter by year, country or segment.

If you want to reproduce the exact dashboard appearance, the notebook includes plotting style settings (colors, fonts and layout) to match the screenshot.

## Requirements & Setup

Install the minimal Python packages used by the notebook. From the project folder run:

```powershell
pip install pandas numpy matplotlib seaborn plotly jupyterlab ipywidgets
```

Notes:

- Use `jupyter lab` or `jupyter notebook` to open `Sales_&_Customer_Analysis.ipynb`.
- If you prefer static charts only, `matplotlib` and `seaborn` are sufficient. For interactive charts, enable `plotly`.

## How to run

1. Start Jupyter Lab or Notebook:

```powershell
jupyter lab
```

2. Open `Sales_&_Customer_Analysis.ipynb` and run cells top-to-bottom.

3. To reproduce dashboard numbers and visuals, run the data-cleaning cells first, then the KPI and visualization cells.

## Reproducibility tips

- Ensure the `OrderDate` parsing uses the correct format. If dates fail to parse, inspect the CSV for inconsistent formats.
- Confirm `Sales` and `Profit` are numeric types; convert strings with currency symbols to floats if necessary.
- If charts look clipped, increase figure size in the plotting cells.

## Assumptions & Notes

- Example KPI values in the screenshot (like 118.73M sales) are illustrative samples from the dataset; your numbers may differ depending on data filtering.
- Product and segment names shown in the image are present in the sample dataset; if your dataset uses different labels, update the notebook mapping or groupings.

## Next steps (ideas)

- Add automated tests or small verification cells to assert totals after cleaning.
- Export dashboard visuals to PNG/SVG for reporting.
- Convert notebook into a reproducible script or a small Streamlit/Plotly Dash app for sharing.

---

If you want, I can also:

- add a `requirements.txt` or `environment.yml` for the project,
- modify the notebook to use `plotly` interactivity, or
- create a small Streamlit dashboard that reproduces the layout.
