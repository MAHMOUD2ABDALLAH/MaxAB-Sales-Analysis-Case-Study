# Sales Development Analyst Case Study

This repository analyzes retail visit and order data to evaluate agent performance, customer behavior, and overall business efficiency using Excel Power Query, PivotTables, and formulas.

## Dataset Overview

### 1. **Visits Table**
| Column Name        | Description                               |
|--------------------|-------------------------------------------|
| `visit_id`         | Unique identifier for each visit          |
| `agent_id`         | Sales agent involved in the visit         |
| `retailer_id`      | Unique retailer visited                   |
| `visit_date`       | Date of the visit                         |
| `start_time`       | Visit start time                          |
| `arrive_time`      | Agent arrival time                        |
| `end_time`         | Visit end time                            |
| `visit_reason`     | Reason for the visit                      |
| `manager_id`       | Sales manager responsible                 |

### 2. **Orders Table**
| Column Name              | Description                            |
|--------------------------|----------------------------------------|
| `order_id`               | Unique order identifier                |
| `order_date`             | Timestamp of order creation            |
| `nmv`                    | Net Merchandise Value                  |
| `retailer_id`            | Retailer placing the order             |
| `sales_status_id`        | Status identifier (e.g., delivered)    |
| `order_status_description` | Textual status of the order         |

---

##  Tools Used
- **Microsoft Excel**
- **Power Query**
- **PivotTables**
- **Excel Formulas**

---

## Analysis & Methodology

### **Question 1: Orders Associated with Agents**
**Goal:** Count how many orders are associated with agents on days they visited the retailer.

**Steps:**
1. Extract date from `visit_date` and `order_date`.
2. Merge `visits` and `orders` on:
   - `retailer_id`
   - `visit_date` = `order_date`
3. Group by `agent_id`, count `order_id`.

**Output Table:**
| Agent ID                                                            | Orders Count | NMVs  Sum |
|---------------------------------------------------------------------|--------------|-----------|
| 004bbd803a926c3608f6c04a7a47221a4fb8badf3f37ffcbe1a2f24d42ec0550    | 5973         |3413737.481|

          |





<img width="997" alt="image" src="https://github.com/user-attachments/assets/92d847ab-b5a0-4d05-9ae7-6f898434c402" />

---

### **Question 2: Strike Rate per Agent**
**Formula:**  
```excel
Strike Rate = (Orders Count / Visits Count) * 100
```

**Steps:**
- Pivot 1: Count `visit_id` by `agent_id`
- Pivot 2: Orders Count from Q1
- Combine for final strike rate calculation

| Agent ID | Visits Count | Orders Count | Strike Rate (%) |
|----------|---------------|--------------|------------------|
| AG001    | 20            | 12           | 60%              |

---

### **Question 3: Ticket Size per Agent**
**Formula:**
```excel
Ticket Size = Total NMV / Orders Count
```

**Steps:**
- Group by `agent_id`, sum `nmv`
- Join with `Orders Count` to compute

| Agent ID | Total NMV | Orders Count | Ticket Size |
|----------|-----------|--------------|-------------|
| AG001    | $1,200    | 12           | $100        |

---

### **Question 4: Organic vs. Inorganic Activations (Daily)**
**Definitions:**
- **Organic:** First order placed without a visit on the same day
- **Inorganic:** First order placed on the same day as a visit

**Steps:**
1. Group orders by `retailer_id`, get first `order_date`.
2. Merge with `visits` on `retailer_id` and compare dates.
3. Add flag:
```excel
= IF([Visit Date] = [Order Date], "Inorganic", "Organic")
```

| Date       | Organic | Inorganic |
|------------|---------|-----------|
| 2023-10-01 | 5       | 8         |

---

### **Question 5: Retention Rate per Month**
**Formula:**
```excel
Retention Rate = (Repeat Retailers / Active Retailers) * 100
```

**Steps:**
- Identify retailers with >1 order per month
- Distinct count of active retailers

| Month   | Active Retailers | Repeat Retailers | Retention Rate (%) |
|---------|------------------|------------------|---------------------|
| Oct-23  | 50               | 30               | 60%                 |

---

### **Question 6: Retailer Segmentation**
**Metric:**
- Based on `Total Orders`, `Total NMV`, and `Last Order Date`

**Segmentation Logic:**
```excel
= IF(AND([Total Orders] > 5, [Total NMV] > $500), "High-Value Loyal", "Low-Value New")
```

| Retailer ID | Segment           |
|-------------|-------------------|
| RT001       | High-Value Loyal  |

---

## General Methodology

### Power Query
- **Merge Queries** on shared keys (e.g., `retailer_id`)
- **Date Extraction:** Use `DateTime.Date([datetime])`
- **Group By** for aggregations
- **Add Columns** for flags or custom metrics

### PivotTables
- **Rows:** Dimensions like `agent_id`, `order_date`
- **Values:** Metrics like count of `order_id`, sum of `nmv`
- **Filters:** Time range, activation type, etc.

---

## Notes
- Ensure all date fields are properly formatted in Power Query before merging.
- Always validate data consistency across tables post-merge.
- Update PivotTables when source data changes.

---

Let me know if you'd like a downloadable `.md` file version or a GitHub-ready copy with folder structure scaffolding.
