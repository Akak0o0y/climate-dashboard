

---



\## `ROADMAP.md`



```markdown

\# Roadmap – Sustainable Climate Analytics Dashboard



This document tracks how the project can grow from a simple notebook into a more serious climate analytics tool.



---



\## v0.1 – Current State



\- \[x] Load `GlobalLandTemperaturesByCity.csv`

\- \[x] Clean missing values and duplicates

\- \[x] Basic descriptive statistics and distributions

\- \[x] Yearly global/country/city temperature trend

\- \[x] KMeans climate clustering (3 clusters)

\- \[x] Gradio dashboard with:

&nbsp; - Yearly trend tab

&nbsp; - City time series tab

&nbsp; - Cluster overview tab



---



\## v0.2 – Stronger Analysis



\- \[ ] Add more EDA:

&nbsp; - Monthly/seasonal averages per region

&nbsp; - Boxplots or density plots by region/cluster

\- \[ ] Explicitly compute and plot \*\*temperature anomalies\*\* relative to a baseline

\- \[ ] Compare trends for different regions or continents

\- \[ ] Add more statistics in the text summaries (min/max, slope, etc.)



---



\## v0.3 – Better Clustering \& Features



\- \[ ] Try different numbers of clusters `k` and compare results

\- \[ ] Add more features:

&nbsp; - Temperature variance per city

&nbsp; - Seasonal amplitude (difference between hottest/coldest months)

\- \[ ] Evaluate cluster quality using:

&nbsp; - Silhouette score

&nbsp; - Inertia curves (elbow method)

\- \[ ] Give each cluster a human-readable label (e.g., “cold-stable”, “hot-variable”, etc.)



---



\## v0.4 – Visualization Upgrades



\- \[ ] Add interactive plots (hover tooltips, zoom) with libraries like Plotly

\- \[ ] Show \*\*maps\*\* of cities colored by cluster (using latitude/longitude if available)

\- \[ ] Add a panel that lists cities per cluster with basic stats

\- \[ ] Export plots as PNG/SVG for reports



---



\## v0.5 – Refactoring \& Structure



\- \[ ] Move logic from the notebook into Python modules:

&nbsp; - `data\_loader.py`

&nbsp; - `features.py`

&nbsp; - `clustering.py`

&nbsp; - `dashboard.py`

\- \[ ] Keep the notebook mainly for exploration and documentation

\- \[ ] Add basic unit tests for core functions (data cleaning, feature generation)



---



\## v1.0 – Small “Product” Version



\- \[ ] Package the dashboard as a standalone app (e.g., `app.py`)

\- \[ ] Add config files to control:

&nbsp; - Time ranges

&nbsp; - Number of clusters

&nbsp; - Filters

\- \[ ] Deploy online:

&nbsp; - Hugging Face Spaces, or

&nbsp; - Simple VPS / cloud instance

\- \[ ] Write a short user guide:

&nbsp; - What the app does

&nbsp; - How to interpret the graphs

&nbsp; - What the clusters mean



---



\## Future Ideas



\- \[ ] Combine with other climate datasets (CO₂, sea level, etc.)

\- \[ ] Add forecasting models for future temperatures

\- \[ ] Explore anomaly detection for extreme events

\- \[ ] Add multi-language support for the UI

\- \[ ] Turn it into a learning resource for people new to data + climate analytics



