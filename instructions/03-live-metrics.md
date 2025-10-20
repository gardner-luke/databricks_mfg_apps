# 📈 Add Live Metrics to Dashboard

Use the **Apps Cookbook – Read Tables** approach (no SQL in this prompt):  
https://apps-cookbook.dev/docs/streamlit/tables/tables_read

**Placeholders (required):**
- UC table: `demos_genie.dbdemos_iot_platform.turbine_training_dataset` (format `catalog.schema.table`)
- SQL Warehouse **ID**: `4b9b953939869799` (ID only)

**Columns used:** `turbine_id`, `abnormal_sensor`, `hourly_timestamp`, `state`, `location`

**Home page – simple spec:**
- If placeholders aren’t set, show inputs for `<UC_TABLE>` and `<WAREHOUSE_ID>`.
- Read data via the Cookbook method.

**Point-in-time KPIs (for the selected day):**
- First **dedupe to one record per `turbine_id`** using the **max `hourly_timestamp`** within that day.
- **AUM** = distinct `turbine_id`
- **OK Turbines** = `abnormal_sensor = 'ok'`
- **OK %** = OK / AUM

**Charts:**
1) **Timeline (hourly)** – **OK % vs Not-OK % by `state`** for the selected day  
   - Group by `state` and `hourly_timestamp` (hour granularity).  
   - Compute % from counts of `abnormal_sensor` (`ok` vs `not ok`).  
   - Include a simple **state multi-select** (all states selected by default).

2) **Bar chart: Turbines by `location`**  
   - Use the **deduped latest** records for the selected day.  
   - Show count by `location`

**Structure:**  
- Keep Streamlit’s built-in multipage setup; only the **Home** page is used here.  
- Keep everything minimal; follow the Cookbook connection pattern exactly.