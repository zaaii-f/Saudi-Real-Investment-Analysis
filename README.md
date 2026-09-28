# Strategic Analysis Dashboard for Real Estate Investment Indicators using Power BI and DAX 📊

> **Note:** This project was built using **synthetic data** to showcase analytical skills and calculation modeling. It does not represent actual figures.

---

## 🌐 Project Description
An analytical project that studies the real estate market in Saudi Arabia by tracking key performance indicators (KPIs). The work focuses on analyzing the distribution of property sectors, monitoring price changes, and measuring annual growth rates across regions and neighborhoods, to give a clear view of investment market trends.

## 🛠️ Tools Used
- **Power BI:** Designing interactive report pages and building dashboards.
- **DAX:** Building advanced calculations that process the data and extract the indicators.
- **Power Query:** Cleaning and structuring the data before analysis.
- **Excel:** The main source of the synthetic data used.

## 🧠 Calculation Models (DAX Measures)
The business logic was built with DAX to extract precise details. Here are a few examples:

### 1. Highest Annual Growth Rate
Measures the largest jump in annual change:
```
[Max Annual Growth Rate] = 
MAX('SHEET 1'[Annual Change Rate (%)]) / 100
```

### 2. Region with the Lowest Growth Rate
Uses variables to identify the lowest-performing region based on the filter context:
```
[Region with Lowest Growth Rate] = 
VAR MinRate = MINX(ALL('SHEET 1'), 'SHEET 1'[Annual Change Rate (%)])
RETURN
CALCULATE(
    SELECTEDVALUE('SHEET 1'[Region / City]),
    FILTER(
        ALL('SHEET 1'),
        'SHEET 1'[Annual Change Rate (%)] = MinRate
    )
)
```

### 3. Top 5 Neighborhoods by Price
Extracts a descending list of the 5 most expensive neighborhoods by average price per square meter, to identify market trends:
```
TOP5 = 
TOPN(
    5,
    'SHEET 1',
    'SHEET 1'[Average Price (SAR/m²)],
    DESC
)
```

## 💡 Key Insights
 * The residential sector holds the largest share of the property distribution, at 62.35%.
 * Identified the areas with the highest annual growth rate, at 7.65% (for example, Al Nakheel neighborhood).
 * Highlighted the price gap between major cities to support investment positioning decisions.

## 🖼️ Dashboard Preview
![Dashboard Preview](https://github.com/user-attachments/assets/e9c09007-4bee-40b7-b6de-4e84ff2b7c0e)

## 📁 Data File
[📁 Download the real estate data file (Excel)](realestate_data.xlsx)