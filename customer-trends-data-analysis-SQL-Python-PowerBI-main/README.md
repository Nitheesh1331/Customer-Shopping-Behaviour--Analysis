# Customer Shopping Behavior Analysis

## 📌 Project Overview
This project analyzes customer shopping behavior using transactional data from 3,900 purchases across various product categories. By leveraging **Python** for data engineering, **PostgreSQL** for deep-dive analytical querying, and **Power BI** for visual reporting, this project uncovers actionable insights into spending patterns, customer segments, product preferences, and subscription behavior to guide strategic business decisions.

Detailed summaries and visual dashboards can be referenced in the main documentation file named `Customer Shopping Behavior Analysis.pdf`.

---

## 📊 Dataset Summary
* **Total Records:** 3,900 rows
* **Features:** 18 columns covering:
  * **Demographics:** Age, Gender, Location, Subscription Status
  * **Purchase Details:** Item Purchased, Category, Purchase Amount (USD), Season, Size, Color
  * **Behavioral Data:** Discount Applied, Promo Code Used, Previous Purchases, Frequency of Purchases, Review Rating, Shipping Type
* **Data Quality Note:** Handled 37 missing values in the `Review Rating` column during pre-processing.

---

## 🛠️ Data Pipeline & Exploratory Data Analysis (Python)
The initial phase involved rigorous data preparation and cleaning using Python (`pandas`):

* **Data Cleaning & Imputation:** Identified missing data and imputed the null entries in the `Review Rating` column using the median rating of each specific product category.
* **Standardization:** Converted all column names to standard `snake_case` format for seamless database integration and querying readability.
* **Feature Engineering:** 
  * Created an `age_group` column by binning customer ages into cohorts (*Young Adult, Adult, Middle-aged, Senior*).
  * Synthesized a `purchase_frequency_days` column from behavioral data.
* **Redundancy Filtering:** Conducted a consistency check between `discount_applied` and `promo_code_used`. Found high alignment and dropped `promo_code_used` to optimize data efficiency.
* **Database Pipeline:** Established a secure connection to a PostgreSQL database instance and exported the fully cleaned DataFrame into unified SQL tables.

---

## 🔍 Data Analysis & Insights (SQL)
Using **PostgreSQL**, the following structured business questions were answered:

### 1. Revenue by Gender
* **Female:** \$75,191
* **Male:** \$157,890 *(Significantly higher volume/spend driven by male demographics)*

### 2. High-Spending Discount Users
* Identified **839 customers** who leveraged a discount but still maintained an individual purchase amount above the company-wide average.

### 3. Product Performance Metrics
* **Top 5 Products by Average Rating:** Gloves (3.86), Sandals (3.84), Boots (3.82), Hat (3.80), Skirt (3.78).
* **Top 5 Discount-Dependent Products (Highest % of discount-driven sales):** Hat (50.00%), Sneakers (49.66%), Coat (49.07%), Sweater (48.17%), Pants (47.37%).

### 4. Shipping & Logistics Impact
* **Standard Shipping Avg Spend:** \$58.46
* **Express Shipping Avg Spend:** \$60.48 *(Express shipping correlates with higher transaction values)*

### 5. Subscription Status Performance
| Subscription Status | Total Customers | Avg Spend | Total Revenue |
| :--- | :---: | :---: | :---: |
| **Yes** | 1,053 | \$59.49 | \$62,645.00 |
| **No** | 2,847 | \$59.87 | \$170,436.00 |

### 6. Customer Segmentation
Customers were classified based on their lifetime purchase history:
* **Loyal Customers:** 3,116
* **Returning Customers:** 701
* **New Customers:** 83

### 7. Revenue Generation by Age Group
* **Young Adult:** \$62,143
* **Middle-aged:** \$59,197
* **Adult:** \$55,978
* **Senior:** \$55,763

---

## 📉 Interactive Power BI Dashboard
An interactive executive dashboard was constructed to track critical KPIs and retail metrics dynamically.

### Key Visualizations Included:
* **High-Level KPIs:** Total Customers (3.9K), Average Purchase Amount (\$59.76), Average Review Rating (3.75).
* **Subscription Breakdown:** A donut chart showing a 27% Subscription vs. 73% Non-Subscription user distribution.
* **Category Performance:** Vertical bar charts isolating **Clothing** and **Accessories** as major revenue engines compared to Footwear and Outerwear.
* **Demographic Drills:** Dual horizontal charts mapping out Revenue and Sales volumes across binned age categories.

---

## 🚀 Strategic Business Recommendations

* **Boost Subscription Adoption:** With subscribers making up only 27% of the customer base, introducing tiered loyalty rewards or exclusive subscriber-only discounts could convert the 73% non-subscriber majority.
* **Targeted Marketing Campaigns:** Allocate higher marketing spend toward the **Young Adult** demographic and **Male** segments, as they represent the largest gross revenue blocks.
* **Discount Optimization Strategy:** Products like *Hats* and *Sneakers* are highly discount-dependent (nearly 50%). Transition these items toward value-bundle marketing to protect profit margins.
* **Logistics Monetization:** Since Express Shipping users spend more on average, introduce a lower free-express-shipping threshold on high-margin items to boost Average Order Value (AOV).

---

## 📂 Repository Structure
```text
├── data/                  # Raw and Cleaned Datasets
├── python/                # Jupyter Notebooks for EDA, Cleaning, and DB Upload
├── sql/                   # PostgreSQL Scripts with Business Queries
├── dashboard/             # Power BI Desktop File (.pbix) and Screenshots
└── README.md              # Project Documentation
```
