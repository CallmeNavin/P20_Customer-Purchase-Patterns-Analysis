# P20_Customer-Purchase-Patterns-Analysis

**VERSION 1**

**A. Project Overview**

- This project applies Market Basket Analysis on the Online Retail dataset to uncover product associations and identify opportunities for cross-selling and bundling.

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

- Although three ranking tables were generated (by Support, Confidence, and Lift), this project focuses primarily on Lift for deriving insights:
  + Support only shows how frequently items appear, but in this dataset, even the top itemsets have support <3%. Hence, support values are too low to reveal meaningful patterns.
  + Confidence indicates the probability of buying B given A, but it can be misleading if item A is rare. For example, very high confidence may arise simply because a niche item always appears with another, not because of a strong relationship.
  + Lift corrects for this by measuring how much stronger the co-occurrence of A and B is compared to random chance. A lift >> 1 reveals a true association.
→ Therefore, Lift is the most reliable measure here. With values exceeding 50, the results highlight extremely strong product associations such as:
- Regency Tea Collection (Plates, Jugs, Bowls) almost always purchased together → strong bundle potential. Customers mix colors (Green ↔ Pink ↔ Roses) instead of sticking with one color, showing cross-color affinity.
- Poppy’s Playhouse series (Bedroom, Kitchen, Livingroom) consistently appear together → strong case for upselling full playhouse kits.

_**Actionable Plans**_

- Bundle Strategy - Regency Tea Collection:
  + Promote themed bundles by color (e.g., Green + Pink).
  + Offer small discounts (5–10%) for purchasing the entire set.
- Cross-Selling - Poppy’s Playhouse Series:
  + Online: add “Frequently Bought Together” suggestions when a customer selects one item.
  + Offline: display Kitchen, Bedroom, Livingroom items together to encourage full-set purchases.

**E. Appendix**

- Top 10 by Support

| Antecedents                   | Consequents                   | Support | Confidence | Lift  |
| ----------------------------- | ----------------------------- | ------- | ---------- | ----- |
| JUMBO BAG RED RETROSPOT       | JUMBO BAG PINK POLKADOT       | 0.029   | 0.341      | 7.26  |
| JUMBO BAG PINK POLKADOT       | JUMBO BAG RED RETROSPOT       | 0.029   | 0.627      | 7.26  |
| GREEN REGENCY TEACUP & SAUCER | ROSES REGENCY TEACUP & SAUCER | 0.029   | 0.783      | 18.53 |
| ROSES REGENCY TEACUP & SAUCER | GREEN REGENCY TEACUP & SAUCER | 0.029   | 0.691      | 18.53 |
| ALARM CLOCK BAKELIKE GREEN    | ALARM CLOCK BAKELIKE RED      | 0.029   | 0.672      | 14.19 |
| ALARM CLOCK BAKELIKE RED      | ALARM CLOCK BAKELIKE GREEN    | 0.029   | 0.604      | 14.19 |
| LUNCH BAG RED RETROSPOT       | LUNCH BAG PINK POLKADOT       | 0.028   | 0.406      | 8.08  |
| LUNCH BAG PINK POLKADOT       | LUNCH BAG RED RETROSPOT       | 0.028   | 0.562      | 8.08  |
| LUNCH BAG RED RETROSPOT       | LUNCH BAG BLACK SKULL         | 0.028   | 0.401      | 7.07  |
| LUNCH BAG BLACK SKULL         | LUNCH BAG RED RETROSPOT       | 0.028   | 0.491      | 7.07  |

- Top 10 by Confidence

| Antecedents                                       | Consequents                   | Support | Confidence | Lift  |
| ------------------------------------------------- | ----------------------------- | ------- | ---------- | ----- |
| Poppy’s Playhouse Bedroom + Livingroom            | Poppy’s Playhouse Kitchen     | 0.010   | 0.907      | 48.60 |
| Regency Cakestand + Roses Regency Teacup & Saucer | Green Regency Teacup & Saucer | 0.013   | 0.902      | 24.19 |
| Regency Tea Plate Pink                            | Regency Tea Plate Green       | 0.011   | 0.902      | 61.90 |
| Roses Regency Teacup & Saucer + Pink Regency Cup  | Green Regency Teacup & Saucer | 0.021   | 0.894      | 23.99 |
| Green Regency Teacup & Saucer + Cakestand         | Roses Regency Teacup & Saucer | 0.013   | 0.882      | 20.87 |
| Regency Tea Plate Pink                            | Regency Tea Plate Roses       | 0.011   | 0.879      | 49.69 |
| Regency Cakestand + Pink Regency Teacup           | Green Regency Teacup & Saucer | 0.015   | 0.877      | 23.52 |
| Poppy’s Playhouse Kitchen + Livingroom            | Poppy’s Playhouse Bedroom     | 0.010   | 0.865      | 50.74 |
| Regency Cakestand + Pink Regency Cup              | Roses Regency Teacup & Saucer | 0.014   | 0.858      | 20.30 |
| Poppy’s Playhouse Livingroom                      | Poppy’s Playhouse Kitchen     | 0.012   | 0.853      | 45.70 |

- Top 10 by Lift

| Antecedents                       | Consequents                       | Support | Confidence | Lift  |
| --------------------------------- | --------------------------------- | ------- | ---------- | ----- |
| Regency Tea Plate Green           | Regency Tea Plate Pink            | 0.011   | 0.748      | 61.90 |
| Regency Tea Plate Pink            | Regency Tea Plate Green           | 0.011   | 0.902      | 61.90 |
| Poppy’s Playhouse Livingroom      | Poppy’s Playhouse Kitchen+Bedroom | 0.010   | 0.738      | 53.85 |
| Poppy’s Playhouse Kitchen+Bedroom | Poppy’s Playhouse Livingroom      | 0.010   | 0.732      | 53.85 |
| Regency Sugar Bowl Green          | Regency Milk Jug Pink             | 0.011   | 0.769      | 52.37 |
| Regency Milk Jug Pink             | Regency Sugar Bowl Green          | 0.011   | 0.757      | 52.37 |
| Poppy’s Playhouse Kitchen+Living  | Poppy’s Playhouse Bedroom         | 0.010   | 0.865      | 50.74 |
| Poppy’s Playhouse Bedroom         | Poppy’s Playhouse Kitchen+Living  | 0.010   | 0.589      | 50.74 |
| Regency Tea Plate Roses           | Regency Tea Plate Pink            | 0.011   | 0.601      | 49.69 |
| Regency Tea Plate Pink            | Regency Tea Plate Roses           | 0.011   | 0.879      | 49.69 |

**About Me**

Hi, I'm Navin (Bao Vy) – an aspiring Data Analyst passionate about turning raw data into actionable business insights. I’m eager to contribute to data-driven decision making and help organizations translate analytics into business impact. For more details, please reach out at:

🌐 LinkedIn: https://www.linkedin.com/in/navin826/

📂 Portfolio: https://github.com/CallmeNavin/
