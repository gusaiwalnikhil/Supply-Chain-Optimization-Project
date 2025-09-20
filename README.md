# Supply Chain Optimization Using Python

A project exploring supply chain cost‑optimization using linear
programming, scenario analysis, and data visualization. It considers
multiple plants, countries, capacities, and cost structures to determine
lowest‐cost supply options under constraints.

------------------------------------------------------------------------

##  Table of Contents

1.  [Project Overview](#project-overview)\
2.  [Data / Inputs](#data--inputs)\
3.  [Assumptions](#assumptions)\
4.  [Methodology](#methodology)\
5.  [Implementation Details](#implementation-details)\
6.  [Usage](#usage)\
7.  [Key Outputs and Visualizations](#key-outputs-and-visualizations)

------------------------------------------------------------------------

##  Project Overview

This project aims to model a supply chain network spanning 5 different
countries, with a mix of **low‑capacity and high‑capacity plants**.

The goal is to satisfy consumer demand across the countries while
minimizing total cost (production + transportation + storage etc.),
considering various constraints like plant capacities, delivery lead
times, freight costs, and emission costs. Scenario comparisons are
enabled via interactive widgets.

------------------------------------------------------------------------

##  Data / Inputs

The repository includes several Excel files containing the data needed
for modelling:

  ----------------------------------------------------------------------------
  File                        Description
  --------------------------- ------------------------------------------------
  `demand.xlsx`               Consumer demand for each country.

  `capacity.xlsx`             Production capacities of plants.

  `fixed_cost.xlsx`           Fixed production costs (monthly) per plant.

  `variable_costs.xlsx`       Variable production costs per unit.

  `freight_costs.xlsx`        Transportation costs between plants / countries.

  `storage_costs.xlsx`        Costs for holding inventory (derived from fixed
                              costs).

  `Delivery_LeadTime.xlsx`    Lead times for deliveries (shipping +
                              within‑country).

  `Delivery_Deadlines.xlsx`   Expected deadline dates for deliveries.

  `CO2_Emissions.xlsx`        Data needed for emission cost / CO2 calculation.

  `Total_Data.xlsx`           Aggregated dataset combining relevant inputs.
  ----------------------------------------------------------------------------

------------------------------------------------------------------------

##  Assumptions

-   Storage costs are assumed to be 10% of fixed costs per year. Given
    fixed costs are monthly, storage cost per day per unit is derived by
    dividing appropriately.\
-   Freight / shipping is assumed to happen only via sea freight.\
-   CO₂ emissions from shipping: calculations assume that diesel engine
    consumption yields 2640 g of CO₂ per liter, and that on average a
    cargo ship travels so that 1 km movement contributes \~10.82 g CO₂
    per ton using provided conversion details.\
-   For delivery lead times: a standard of **3 days within country** for
    intra‑country movement + added time based on shipping between ports
    of origin.\
-   Specific ports are assumed for each country, e.g. Port of New York
    (USA), Port of Hamburg (Germany), Port of Tokyo (Japan), Port of
    Santos (Brazil), Port of Mumbai (India).

------------------------------------------------------------------------

##  Methodology

1.  **Linear Programming Model**\
    Use optimization to minimize cost. Decision variables include how
    much each plant produces, how much is shipped to each country,
    storage held etc.

2.  **Cost Components**

    -   Fixed production cost\
    -   Variable cost per unit produced\
    -   Transportation / freight costs\
    -   Storage costs\
    -   Emission costs (CO₂)

3.  **Constraints**

    -   Plant capacity limits\
    -   Demand must be met in each country\
    -   Delivery lead times and deadlines

4.  **Scenario Analysis**\
    Parameters can be tweaked (e.g., costs, lead times, capacity) to
    compare scenarios. Interactive elements (widgets) allow for
    comparison.

5.  **Visualization**\
    Charts / tables to show cost breakdowns, shipping flows, emissions,
    how costs vary under different assumptions.

------------------------------------------------------------------------

## 🛠 Implementation Details

-   **Environment**: Jupyter Notebook
    (`Supply Chain Optimization.ipynb`)\
-   **Libraries likely used**:
    -   Pandas / NumPy for data handling\
    -   PuLP or SciPy for optimization\
    -   Matplotlib / Seaborn / Plotly for visualization\
    -   ipywidgets for interactivity
-   **Workflow**:
    -   Read data from the Excel files\
    -   Preprocess data to compute derived fields (e.g. storage cost per
        unit/day, emission factors)\
    -   Build optimization model using defined cost function and
        constraints\
    -   Solve for minimum total cost\
    -   Analyze results and visualize

------------------------------------------------------------------------

##  Usage

To run / reproduce this project:

1.  Clone the repository.\

2.  Install dependencies. Example:

    ``` bash
    pip install pandas numpy openpyxl pulp matplotlib ipywidgets
    ```

3.  Ensure all `.xlsx` data files are present in the working directory.\

4.  Open and run `Supply Chain Optimization.ipynb` from top to bottom.\

5.  Use widgets (if available) to adjust scenarios and observe results.

------------------------------------------------------------------------

## 📊 Key Outputs and Visualizations

-   Minimum total cost for satisfying demands across all countries.\
-   Cost breakdown: production, transportation, storage, CO₂ emissions.\
-   Shipping / logistics flows: how much each plant supplies to each
    country.\
-   Emission estimates (CO₂) associated with freight.\
-   Sensitivity / scenario outputs: what happens when capacities or
    freight costs change.

------------------------------------------------------------------------
