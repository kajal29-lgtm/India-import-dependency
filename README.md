# India's Import Dependency: China, Russia and the USA (FY 2024-25 vs 2025-26)

How dependent is India on three major suppliers, and in which products does that dependency become a strategic risk?

This project measures, product by product (HS 2-digit chapters), how much of India's imports come from **China, Russia and the USA**, flags the chapters where a single country supplies a very large share, and compares **FY 2024-25 with FY 2025-26**.

**Author:** Kajal Maurya
**Tools:** Excel (cleaning) · Python / pandas in Google Colab (analysis) · SQLite / DB Browser (queries) · Power BI (dashboard)

---

## Key questions

1. What share of India's total imports comes from China, Russia and the USA?
2. In which product chapters is India most exposed to a single supplier (share above 30%, 40%, 50%)?
3. How did these shares change between FY 2024-25 and FY 2025-26?
4. What kind of policy tools sit behind these numbers? (See the policy section below.)

## Method

- **Dependency share** = India's imports of a chapter from country *X* ÷ India's total world imports of that chapter.
- For each chapter I record the **top supplier among the three countries** and its share (`top_c`, `top_sh`).
- A chapter is flagged as **concentrated** if one of the three countries supplies more than 30% / 40% / 50% of India's total imports in it.
- Chapters with no import value for a country are filled with 0.
- Values are in US$ million, as reported in the source files.

## Headline results (FY 2025-26)

| Measure | Result |
|---|---|
| China's share of India's total imports | **17.0%** |
| Russia's share | **7.1%** |
| USA's share | **6.9%** |
| Chapters where one of the three supplies >30% | 38 chapters, 34.6% of India's imports |
| Chapters where one of the three supplies >40% | 24 chapters, 20.0% of imports |
| Chapters where one of the three supplies >50% | 17 chapters, 2.0% of imports |

**What stands out**

- **Where dependency is largest in value:** China supplies about **44%** of India's imports of electrical machinery and equipment (HS 85) and about **40%** of machinery and mechanical appliances (HS 84). It also supplies about **45%** of organic chemicals (HS 29). These are inputs to manufacturing, so a disruption would spread through the economy.
- **Where dependency is highest in share:** China supplies roughly 73% of man-made filaments (HS 54) and knitted fabrics (HS 60), and more than 85% of small categories such as umbrellas (HS 66) and prepared feathers/artificial flowers (HS 67). Shares are very high but the values are small.
- **Energy:** Russia supplied about **23.5%** of India's mineral fuel imports (HS 27) in FY 2025-26, down from about 26.0% in FY 2024-25. The USA's share in the same chapter rose from about 6.6% to about 8.5%.
- **China, year on year:** China's imports under HS 85 grew from about 38,027 to 46,365, and its share rose from about 42.9% to 44.2%.
- **USA:** Dependency is concentrated in a few chapters, such as edible fruit and nuts (HS 8, about 24%) and works of art and antiques (HS 97, about 32%), rather than in broad manufacturing inputs.

> Note: "top supplier" is measured only among China, Russia and the USA. Other countries may supply more of a chapter than any of these three.

## Policy lens: how policy shapes (and responds to) these numbers

This section explains the policy context. The data here shows *what* the dependency looks like; it does not by itself prove *why*. The links below are hypotheses to be tested, not results.

| Policy area | How it connects to the data |
|---|---|
| **Tariffs, anti-dumping and quality-control orders** | Trade remedies and technical standards raise the cost of importing particular products and can shift sourcing. Chapters with very high China shares (textiles, glass, ceramics, chemicals) are typical candidates for such measures. |
| **Production-linked incentives (PLI) and Atmanirbhar Bharat** | Aim to build domestic capacity in electronics, machinery, pharmaceuticals and others, so that import dependency in HS 84/85/29 falls over time. A falling share in these chapters would be the thing to watch. |
| **Investment screening (FDI rules for land-border countries, 2020)** | Shapes how Chinese capital and technology enter Indian supply chains, which matters for electronics and machinery dependency. |
| **Energy security and sanctions** | Russia's share in mineral fuels reflects sourcing choices made after Western sanctions and price caps on Russian oil; the USA's rising share reflects diversification and bilateral energy purchases. |
| **Bilateral trade relations and tariffs** | Changes in tariffs or trade deals with the USA and diplomatic relations with China and Russia can move shares quickly between years. |

**Policy questions this project raises**

- Are PLI-supported sectors showing falling China shares, or only rising domestic assembly with the same imported components?
- Is "diversification" real (shares moving to other countries) or just reshuffled between the three countries studied?
- Which dependencies are *strategic* (energy, electronics, active pharmaceutical ingredients) and which are just cheap consumer goods?

## Files in this repository

| File | What it is |
|---|---|
| `imp_china..xlsx`, `imp_Russia.xlsx`, `imp_US.xlsx` | India's imports from China, Russia and the USA by HS chapter (FY 2024-25 and 2025-26) |
| `world_imports25_26.xlsx` | India's total imports from the world by HS chapter |
| `dependency.csv` | Wide format: shares and top supplier per HS chapter |
| `dependency_long.csv` | Long format: HS, commodity, country, financial year, value and share |
| `trade..db`, `query.db` | SQLite databases used for the SQL queries |
| `india's Imports.pbix` | Power BI dashboard |

## How to reproduce

1. Load the four Excel files in Python (pandas). Clean the HS codes, convert values to numbers and merge by HS chapter.
2. Compute each country's share of India's imports per chapter, find the top supplier and flag chapters above 30%, 40% and 50%.
3. Save the output as `dependency.csv`. The long version feeds Power BI.
4. Open the `.pbix` file in Power BI Desktop.

## Limitations

- HS 2-digit chapters are broad; a chapter can hide very different products (e.g. HS 85 covers phones and solar cells).
- Only three suppliers are compared.
- Two financial years only, so trends are indicative.
- Shares are based on import values, which are affected by price changes as well as quantities.

## Data sources

- Ministry of Commerce and Industry, Government of India: TradeStat (Export Import Data Bank, EIDB), tradestat.commerce.gov.in. Country-wise and commodity-wise imports for FY 2024-25 and 2025-26, downloaded in October 2026. Values in US$ million.

---

*Built as part of a one-week data-skills sprint. Feedback welcome.*
