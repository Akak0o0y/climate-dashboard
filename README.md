\# Sustainable Climate Analytics Dashboard



Sustainable Climate Analytics Dashboard is a personal AI/data project that turns raw global temperature data into an interactive dashboard.  

It helps you explore \*\*long-term warming trends\*\*, \*\*city-level temperature history\*\*, and \*\*climate-based clusters of cities\*\* using Python, KMeans clustering, and a Gradio web UI.



---



\## 🎯 Problem Statement



Climate data is huge, noisy, and not intuitive to read directly from CSV files or spreadsheets.



Most people only see headlines like “global warming is increasing,” but they do not have a \*\*simple, interactive way\*\* to:



\- Inspect \*\*how temperatures changed over years\*\* globally or for a specific country/city.

\- Compare \*\*temperature behavior between cities\*\* over time.

\- Group cities into \*\*climate profiles\*\* (e.g., colder vs. hotter climates) in a data-driven way instead of guessing.



So the core problem is:



> How can we take a large historical temperature dataset and turn it into a clean, interactive tool that reveals \*\*trends\*\*, \*\*patterns\*\*, and \*\*climate clusters\*\* in a way that is easy to explore?



---



\## ✅ Solution Overview



This project builds a small end-to-end analytics and AI pipeline on top of the  

\*\*GlobalLandTemperaturesByCity\*\* dataset and exposes it through a \*\*Gradio dashboard\*\*.



\### 1. Data Preparation \& Cleaning



\- Load `GlobalLandTemperaturesByCity.csv`.

\- Inspect head, tail, shape, and basic statistics.

\- Handle missing values:

&nbsp; - Fill missing `AverageTemperature` and `AverageTemperatureUncertainty` with their mean.

&nbsp; - Drop remaining NaNs and duplicates.

\- Convert `dt` to datetime and extract:

&nbsp; - `year`

&nbsp; - `month`



\### 2. Exploratory Data Analysis (EDA)



The notebook runs several analyses:



\- \*\*Distributions\*\* of:

&nbsp; - `AverageTemperature`

&nbsp; - `AverageTemperatureUncertainty`

\- \*\*Time trend\*\*:

&nbsp; - Compute yearly average temperature and plot a \*\*long-term warming trend\*\*.

\- \*\*Correlation\*\* between:

&nbsp; - `AverageTemperature` and `AverageTemperatureUncertainty`.



This gives a first look at how temperatures behave and how uncertain the measurements are.



\### 3. Climate Clustering (KMeans)



To group cities by climate patterns:



1\. Filter to more recent years (e.g., `year >= 1900`) to avoid extremely old data.

2\. Compute \*\*average monthly temperatures\*\* for each `(City, Country, month)`.

3\. Pivot to a table where:

&nbsp;  - Each row = \*\*city\*\*

&nbsp;  - Columns = \*\*12 months\*\*

&nbsp;  - Values = average temperature per month

4\. Drop cities with too many missing months.

5\. Scale features with `StandardScaler`.

6\. Run \*\*KMeans\*\* with `k = 3` clusters.

7\. Attach a `cluster\_label` (e.g., `Cluster\_0`, `Cluster\_1`, `Cluster\_2`) back to the original `df`.



Result: each city gets assigned to a \*\*climate cluster\*\* based on its monthly temperature profile.



\### 4. Interactive Dashboard (Gradio)



The Gradio app exposes three main views:



1\. \*\*Yearly Trend\*\*

&nbsp;  - Filter by \*\*country\*\* and optionally by \*\*city\*\*.

&nbsp;  - Plot yearly average temperature over time.

&nbsp;  - Show a text summary with number of years and what the plot represents.



2\. \*\*City Time Series\*\*

&nbsp;  - Select a specific \*\*city\*\*.

&nbsp;  - Plot the full time series of `AverageTemperature` over date.

&nbsp;  - Show a short summary with number of data points and general behavior.



3\. \*\*Climate Clusters Overview\*\*

&nbsp;  - Use `cluster\_label` column.

&nbsp;  - Count how many cities fall into each cluster.

&nbsp;  - Show a bar chart: \*\*number of cities per cluster\*\*.

&nbsp;  - Show a textual summary listing clusters and city counts.



---



\## 💡 What This Project Does (In Plain Terms)



\- Turns a big historical temperature CSV into something \*\*interactive and visual\*\*.

\- Lets you see:

&nbsp; - Is the world warming over time?

&nbsp; - How does a single city’s temperature behave over the full timeline?

&nbsp; - How many cities fall into each climate pattern (cluster)?

\- Uses \*\*unsupervised learning (KMeans)\*\* to discover climate groups without labels.



---



\## 🌟 Why It’s Useful



\- Quick way to explore climate data without writing new code every time.

\- Shows a \*\*complete mini-pipeline\*\*:

&nbsp; - Data cleaning → feature engineering → clustering → visualization → UI.

\- Good \*\*portfolio piece\*\*:

&nbsp; - Clear problem

&nbsp; - Clear solution

&nbsp; - Real dataset

&nbsp; - Interactive front-end

\- Easy to extend:

&nbsp; - You can add more features, more clusters, or connect other climate datasets later.



---



\## 🧰 Tech Stack



\- \*\*Python\*\*

\- \*\*pandas\*\*, \*\*NumPy\*\* – data handling

\- \*\*matplotlib\*\*, \*\*seaborn\*\* – plotting and EDA

\- \*\*scikit-learn\*\* – `StandardScaler`, `KMeans`

\- \*\*Gradio\*\* – web UI for the dashboard



---



\## 📁 Project Structure (suggested)



```text

.

├── data/

│   └── GlobalLandTemperaturesByCity.csv

├── notebooks/

│   └── CS316\_Project\_Phase2\_Groub\_D.ipynb   # main analysis + dashboard code

├── README.md

└── requirements.txt



