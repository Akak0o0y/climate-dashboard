# Sustainable Climate Analytics Dashboard

Sustainable Climate Analytics Dashboard is a personal AI/data project that turns raw global temperature data into an interactive dashboard.  
It helps you explore **long-term warming trends**, **city-level temperature history**, and **climate-based clusters of cities** using Python, KMeans clustering, and a Gradio web UI.

---

## 🎯 Problem Statement

Climate data is huge, noisy, and not intuitive to read directly from CSV files or spreadsheets.

Most people only see headlines like “global warming is increasing,” but they do not have a **simple, interactive way** to:

- Inspect **how temperatures changed over years** globally or for a specific country/city.
- Compare **temperature behavior between cities** over time.
- Group cities into **climate profiles** (e.g., colder vs. hotter climates) in a data-driven way instead of guessing.

So the core problem is:

> How can we take a large historical temperature dataset and turn it into a clean, interactive tool that reveals **trends**, **patterns**, and **climate clusters** in a way that is easy to explore?

---

## ✅ Solution Overview

This project builds a small end-to-end analytics and AI pipeline on top of the  
**GlobalLandTemperaturesByCity** dataset and exposes it through a **Gradio dashboard**.

### 1. Data Preparation & Cleaning

- Load `GlobalLandTemperaturesByCity.csv`.
- Inspect head, tail, shape, and basic statistics.
- Handle missing values:
  - Fill missing `AverageTemperature` and `AverageTemperatureUncertainty` with their mean.
  - Drop remaining NaNs and duplicates.
- Convert `dt` to datetime and extract:
  - `year`
  - `month`

### 2. Exploratory Data Analysis (EDA)

The notebook runs several analyses:

- **Distributions** of:
  - `AverageTemperature`
  - `AverageTemperatureUncertainty`
- **Time trend**:
  - Compute yearly average temperature and plot a **long-term warming trend**.
- **Correlation** between:
  - `AverageTemperature` and `AverageTemperatureUncertainty`.

This gives a first look at how temperatures behave and how uncertain the measurements are.

### 3. Climate Clustering (KMeans)

To group cities by climate patterns:

1. Filter to more recent years (e.g., `year >= 1900`) to avoid extremely old data.
2. Compute **average monthly temperatures** for each `(City, Country, month)`.
3. Pivot to a table where:
   - Each row = **city**
   - Columns = **12 months**
   - Values = average temperature per month
4. Drop cities with too many missing months.
5. Scale features with `StandardScaler`.
6. Run **KMeans** with `k = 3` clusters.
7. Attach a `cluster_label` (e.g., `Cluster_0`, `Cluster_1`, `Cluster_2`) back to the original `df`.

Result: each city gets assigned to a **climate cluster** based on its monthly temperature profile.

### 4. Interactive Dashboard (Gradio)

The Gradio app exposes three main views:

1. **Yearly Trend**
   - Filter by **country** and optionally by **city**.
   - Plot yearly average temperature over time.
   - Show a text summary with number of years and what the plot represents.

2. **City Time Series**
   - Select a specific **city**.
   - Plot the full time series of `AverageTemperature` over date.
   - Show a short summary with number of data points and general behavior.

3. **Climate Clusters Overview**
   - Use the `cluster_label` column.
   - Count how many cities fall into each cluster.
   - Show a bar chart: **number of cities per cluster**.
   - Show a textual summary listing clusters and city counts.

---

## 💡 What This Project Does (In Plain Terms)

- Turns a big historical temperature CSV into something **interactive and visual**.
- Lets you see:
  - Is the world warming over time?
  - How does a single city’s temperature behave over the full timeline?
  - How many cities fall into each climate pattern (cluster)?
- Uses **unsupervised learning (KMeans)** to discover climate groups without labels.

---

## 🌟 Why It’s Useful

- Quick way to explore climate data without writing new code every time.
- Shows a **complete mini-pipeline**:
  - Data cleaning → feature engineering → clustering → visualization → UI.
- Good **portfolio piece**:
  - Clear problem  
  - Clear solution  
  - Real dataset  
  - Interactive front-end
- Easy to extend:
  - You can add more features, more clusters, or connect other climate datasets later.

---

## 🧰 Tech Stack

- **Python**
- **pandas**, **NumPy** – data handling
- **matplotlib**, **seaborn** – plotting and EDA
- **scikit-learn** – `StandardScaler`, `KMeans`
- **Gradio** – web UI for the dashboard

---

## 📁 Project Structure (suggested)

```text
.
├── data/
│   └── GlobalLandTemperaturesByCity.csv      # kept locally (too large for GitHub)
├── notebooks/
│   └── CS316_Project_Phase2_Groub_D.ipynb    # main analysis + dashboard code
├── README.md
└── requirements.txt
