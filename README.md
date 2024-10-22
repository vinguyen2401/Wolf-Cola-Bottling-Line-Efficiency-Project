# Wolf Cola Bottling Line Efficiency Project

## The Situation

You work as a Production Manager for **Wolf Cola**, a soft drink company that handles all its manufacturing operations in Philadelphia.

## The Assignment

Frank, the former manager, initiated a productivity improvement project for the bottling production line and left an Excel file with the data he collected. Your task is to analyze the productivity and downtime data and find ways to improve the line's efficiency.

### Objectives:
- Calculate line efficiency.
- Identify the main downtime factors.
- Calculate downtime by operator and factor.

## About the Dataset

The dataset covers 38 production batches for 6 soda products from August 29 to September 3, 2024. It includes 4 sheets detailing batch numbers, product information, operators, production start/end times, and downtime information. Each product has a minimum production time, with 4 operators managing the batches. There are 12 downtime factors, each related to either operator or machinery errors, with multiple factors affecting a single batch.

### Data Description:

1. **Line Productivity: Fact Table**
   - Contains details for each batch produced.

| Column      | Data Type | Description                                        |
|-------------|-----------|----------------------------------------------------|
| Date        | Date      | Date the batch was produced                        |
| Product ID  | String    | The product produced in the batch                  |
| Batch       | String    | Unique ID for the batch produced                   |
| Operator    | String    | Production line operator in charge of the batch    |
| Start Time  | Time      | Time the batch production started                  |
| End Time    | Time      | Time the batch production ended                    |

2. **Products: Dimension Table**
   - Contains details on each product.

| Column        | Data Type | Description                                        |
|---------------|-----------|----------------------------------------------------|
| Product       | String    | Unique product ID                                  |
| Flavor        | String    | Soda flavor for the product                        |
| Size          | Integer   | Product size (volume)                              |
| Min Batch Time| Integer   | Minimum time required to produce a batch (no downtime)|

3. **Line Downtime: Fact Table**
   - Contains downtime (in minutes) by factor for each batch.

| Column          | Data Type | Description                                        |
|-----------------|-----------|----------------------------------------------------|
| Batch           | String    | Unique ID for the batch produced                   |
| Downtime Factor | Integer   | Downtime minutes for each factor ID (across columns)|

4. **Downtime Factors: Dimension Table**
   - Contains details on each downtime factor.

| Column        | Data Type | Description                      |
|---------------|-----------|----------------------------------|
| Factor        | Integer   | Unique ID for each downtime factor|
| Description   | String     | Downtime factor description       |
| Operator Error| Boolean    | Is this due to operator error? (Yes/No)|

## Analysis Results:

### Line Efficiency Patterns:

| Metric                | Total | Average    | Minimum | Maximum |
|-----------------------|-------|------------|---------|---------|
| Efficiency            |       | 64%        | 61%     | 67%     |
| Actual Batch Time (min)| 2470  | 65         | 60      | 98      |
| Total Batch Time (min) | 3858  | 101.53     | 60      | 205     |


![Overall line efficiency](https://raw.githubusercontent.com/vinguyen2401/Wolf-Cola-Bottling-Line-Efficiency-Project/main/overall%20efficiency.png)

- Overall line efficiency is **64%**.
- **Mac’s efficiency** is **61%**, which is 3% lower than the average.
- **26 out of 38 batches** are performing at a medium level of efficiency (51-80%).
- **5 batches** have efficiency below 50%, indicating potential problems in the production process.

![Batch Efficiency](https://raw.githubusercontent.com/vinguyen2401/Wolf-Cola-Bottling-Line-Efficiency-Project/main/Batch%20Efficiency.png)

### Downtime Causation:
![Downtime factors](https://raw.githubusercontent.com/vinguyen2401/Wolf-Cola-Bottling-Line-Efficiency-Project/main/Downtime%20Factor.png)

Five of the twelve downtime factors account for 80% of lost production time. Each factor caused over 2 hours of delays. The factors are:
1. **Machine adjustment**
2. **Machine failure**
3. **Inventory shortage**
4. **Batch change**
5. **Coding error**

#### Operator Downtime Impact:

| Downtime Factor       | Charlie | Dee  | Dennis | Mac  |
|-----------------------|---------|------|--------|------|
| Machine adjustment     | 118     | 79   | 120    | 15   |
| Machine failure        | 85      | 36   | 88     | 45   |
| Inventory shortage     | 17      | 85   | 43     | 80   |
| Batch change           | 10      | 20   | 0      | 130  |
| Coding error           | 44      | 30   | 24     | 47   |

- **3 major downtime factors** are related to operator errors.
- **Mac** experiences significant downtime due to **batch changes**.
- **Charlie** and **Dennis** face machine adjustment and failure issues.

## Summary:

- **Overall Efficiency:** Average line efficiency is **64%**. Mac's efficiency is **61%**, slightly below average.
- **Batch Performance:** 26 of 38 batches show medium efficiency (51-80%). 5 batches have efficiency below 50%, indicating areas for improvement.
- **Downtime Analysis:** 80% of downtime is caused by five key factors (machine adjustment, machine failure, inventory shortage, batch change, coding error).
- **Operator Errors:** Downtime due to operator-related issues is linked to machine adjustment, batch changes, and coding errors. Mac has significant downtime from batch changes.

## Recommendations:

1. **Train Operators on Machine Adjustment:** Start with machine adjustment training for all operators.
2. **Special Batch Change Training for Mac:** Provide focused training for Mac on reducing batch change-related downtimes.
3. **Preventive Maintenance:** Apply preventive maintenance to machines and double-check inventory levels to reduce downtime due to machine failure and inventory shortages.
