# Sales Performance Analysis

**Portfolio Project · Business & Finance · R**

> I built this end-to-end in R — cleaned the data, ran the numbers, and turned 192 sales records into clear, actionable business findings.

| | |
|---|---|
| **Tools Used** | R, tidyverse, ggplot2 |
| **Dataset** | 192 transactions · 12 months |
| **Focus Areas** | Statistical Analysis · Visualisation |
| **Industry** | Business / Finance |

---

## 01 — Project Overview

I took **192 sales transactions** — a full year of data across four regions and three product lines — and built a complete analysis from scratch in R. The question I set out to answer was simple: where is this business performing, and where is it not?

I used **tidyverse** for all the data wrangling and **ggplot2** for the charts. No shortcuts — every step is structured, documented, and reproducible. The output is a set of clear findings backed by numbers, not guesswork.

---

## 02 — Key Findings

| Metric | Value |
|---|---|
| Total revenue across all regions | **£2.8M** |
| Revenue growth Jan → Dec | **+34%** |
| Distinct product lines analysed | **3** |

The West region came out on top — highest total revenue, strongest growth. The North underperformed across the board. That's not a small gap either; it points to a real structural difference in either sales effort or market opportunity.

> **Standout finding:** Product C has the highest unit price at £79.99, yet it drove the largest share of total revenue. Customers weren't being put off by the price — which tells me the business is underinvesting in pushing its most profitable product.

On discounting: I found that 20% discounts didn't reliably produce higher unit volumes. The business is giving away margin without getting the volume in return. That's a fixable problem.

---

## 03 — My Approach

I broke the work into five stages: inspect the data, engineer the metrics I needed, calculate grouped summaries, build the visuals, and export the results. Clean, repeatable, no mess.

The core of the analysis runs through **dplyr's group_by and summarise pipeline**. Here's exactly how I calculated regional revenue — accounting for discount rates before aggregating:

```r
# Calculate revenue after discount, then summarise by region
region_summary <- sales_data %>%
  mutate(
    revenue = units_sold * unit_price * (1 - discount_pct / 100)
  ) %>%
  group_by(region) %>%
  summarise(
    total_revenue    = sum(revenue),
    avg_units        = mean(units_sold),
    num_transactions = n()
  ) %>%
  arrange(desc(total_revenue))
```

For the charts, I used **ggplot2's layered approach** — building each visual up from scratch so I had full control over layout, colour, labelling, and scale. No default charts that look like every other analysis.

---

## 04 — Visualisations

Four charts, each answering a specific business question. Built in ggplot2 — every element intentional.

### Chart 1 — Monthly Revenue Trend
*Total revenue across all regions · Jan–Dec*

Tracks the overall revenue arc across the year, surfacing seasonal patterns and the sustained upward trend from Q1 to Q4.

### Chart 2 — Revenue by Region
*Ranked highest to lowest · full year total*

Horizontal bar chart comparing the four regions side by side. West leads; North trails significantly.

### Chart 3 — Revenue by Product
*Product C leads despite highest unit price*

Vertical bar chart showing that Product C (£79.99/unit) generated the most revenue — disproving the assumption that higher price means lower uptake.

### Chart 4 — Monthly Revenue by Region (Faceted)
*Each region isolated to surface individual patterns*

A 2×2 faceted panel giving each region its own trend line. This makes it easy to spot where growth is consistent vs. erratic.

---

## 05 — Skills Demonstrated

| Skill | Detail |
|---|---|
| **Data Wrangling** | dplyr · mutate, group_by, summarise, arrange |
| **Data Visualisation** | ggplot2 · geom_line, geom_col, facet_wrap |
| **Statistical Analysis** | Revenue KPIs, discount impact, growth rates |
| **Business Communication** | Translating data findings into actionable insights |

---

*Project 01 / 02 · Sales Performance Analysis · R · tidyverse · ggplot2*
