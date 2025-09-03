<img width="100" height="100" align="right" alt="1652895661maxab-png1652895661" src="https://github.com/user-attachments/assets/3976afc4-6d42-43bc-9223-9975389cb1c5" />

# MaxAB Sales Development Analyst Case Study

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

<img width="997" alt="image" src="https://github.com/user-attachments/assets/92d847ab-b5a0-4d05-9ae7-6f898434c402" />

---

