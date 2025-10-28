# Identifying Unused Communication Scenarios via Logon Comparison

We want to compare how many users have **never logged in** versus those who **have logged in** at least once.  
The actual question is: _Which communication scenarios have never been used?_

To simplify the analysis, we assume a **1:1 relationship**:  
Each **communication user** belongs to exactly **one communication scenario**.  
Therefore, any communication user who has **never logged in** represents a **communication scenario that has never been used**.

---

## Step 1: Create a Responsive Story

To make the story mobile-friendly, we create a **responsive story**.

We insert a **chart component**, drag it into the canvas, and select our pre-defined data source:  
**Query: Communications Query 99**

---

## Step 2: Define the Comparison Using a Bar Chart

We want to compare two user groups using a **bar chart**:

- Users who **have logged in**
- Users who **have never logged in**

To prepare the data, we first need to create a helper measure.

---

### Step 2.1: Create a Calculated Binary Measure

Under **Available**

