# Analysis of Logon Failures

## Objective
In this exercise, we aim to compare the different reasons why a logon - any logon - has failed. These failed events are recorded in the **security audit log**.

As a preparation, we selected and uploaded a dataset from SAP S/4HANA Cloud Public Edition, covering the period **June to end of October**, which includes the following events:
- **AU2**: Logon failed
- **AU4**: Startup transaction failed
- **AU6**: RFC CPIC logon failed
- **AU0**: Logon failed for other reasons
- **BU1**: Password check failed
- **BUD**: Late logon failed

Our goal is to **compare how often each of these failures occurred**.

---

## Steps to Implement

### 1. Create a Responsive Story
We start by creating a **responsive story** (as in the previous exercise) so it can be easily viewed on mobile devices. 

### 2. Add a Bar Chart
We add a **bar chart** to compare the different logon failure reasons by draging the chart onto the widget area. As before, a new window opens. The dataset is already there, so we select **SecurityAuditLogEvents** from there. 


select_sal_events.png
---

## Implementation Details

### Step 4: Create a Helper Measure

As in the previous exercise, we start with creating a helper measure. 
- Go to **Available Objects**.
- Create a helper measure called **Binary Helper** with the value `1`.
- Confirm and close.

binary_helper.png

---

### Step 5: Configure the Bar Chart
We want to see **every failed logon**, and for each failed logon there is a timestamp event. Hence, we're using the timestamp to do our failed-logon count. For this we create a new calculation agan and choose **Aggregation**:

- Aggregate our defined **unique values** (timestamps). This gives us all failed logons. However, we want to filter by type of event, hence we select the event message and apply conditions based on **event message text**.

create_aggregation.png

#### How to Select Conditions:
- Use **Select by Member** to view available members.
- Identify relevant failure reasons. We'll be using five different "logon fails":
  - **Logon failed with reason 1**
  - **Logon failed with reason 2**
  - **Logon failed with reason 52**
  - **Logon failed with reason 53**
  - **Password check failed4** 
  - **RFC/CPIC logon failed**
 
Note: for those failed logon reasons which have more than one entry, select all! So in this example, our first logon failed member  - reason 1 - select the first two event messages. Confirm with **ok** 

select_members.png
---

### Step 6: Create Measures for Each Reason

As you can see after having created the first aggregation, this already gives us the number of failed logons with reason 1. For the subsequent calculations, simply hover the mouse over the three dots of the first aggregation and select **duplicate**

duplicate_calc.png

The only thing you need to change is the selection of members in the event message text. Edit for:
  - Reason 2
  - Reason 52
  - Reason 53
  - Password failures
  - RFC CPIC failures

---

### Step 7: Rename Measures
In our example, we simply duplicated the calculations without renaming them in the same step. Obviously, you can edit the name during the previous (duplicate) step. If you haven't done it then, go into every calculation again and change the names as follows. 

Rename each aggregation for clarity:
- Aggregation 1: Incorrect logon data
- Aggregation 2: User locked
- Aggregation 3: No password
- Aggregation 4: Too many password attempts 
- Aggregation 5: Password check failed
- Aggregation 6: FailedRFC/CPIC  logons

---

## Final Notes
After renaming and verifying all measures, the bar chart will clearly show the frequency of each failure reason. This provides a visual comparison of logon issues across the selected timeframe.
