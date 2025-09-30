# P20_Customer-Purchase-Patterns-Analysis

**VERSION 1**

**A. Project Overview**

- This project applies Market Basket Analysis on a real-world retail dataset to uncover product associations and customer purchase patterns, aiming to support cross-selling strategies and optimize product placement.
- Flow: Transaction table → Basket → Encoding (OneHot) → Apriori/FP-growth → Association Rules (support, confidence, lift) → visualize insight.

**B. Dataset Information**

_**Source**_

- Online Retail Data Set from UCI ML repo
- https://www.kaggle.com/datasets/jihyeseo/online-retail-data-set-from-uci-ml-repo

**_Period_**

- Data covers the period December 2010 to June 2011

**C. Methodology**

- Data Cleaning:
  + Column Type:
    - CustomerID: float → Convert to string
  + %Blank:
    - CustomerID missing ~25% → Drop missing rows
    - Description missing ~0.27% → Fill missing rows by "Unknow"
  + Outliers:
    - Quantity: 10.82% → Drop rows which have Quantity <= 0
    - UnitPrice: 7.31% → Drop rows which have UnitPrice <= 0
  + Duplicate: 0.97% → Drop duplicate rows
  + Convert 'StockCode' column to String
- Export Cleaned Data
- Use FPGrowth for Market Basket Analysis

**D. Key Findings & Actionable Plans**

_**Key Findings**_

- 

_**Actionable Plans**_

- 

**About Me**

Hi, I'm Navin (Bao Vy) – an aspiring Data Analyst passionate about turning raw data into actionable business insights. I’m eager to contribute to data-driven decision making and help organizations translate analytics into business impact. For more details, please reach out at:

🌐 LinkedIn: https://www.linkedin.com/in/navin826/

📂 Portfolio: https://github.com/CallmeNavin/
