# 📈 Add Live Metrics to Dashboard

Use the **Apps Cookbook – Read Tables** approach:  
https://apps-cookbook.dev/docs/streamlit/tables/tables_read

**Placeholders (required):**
- UC table: `demos_genie.dbdemos_iot_platform.turbine_training_dataset` (format `catalog.schema.table`)
- SQL Warehouse **ID**: `4b9b953939869799` (ID only)

**Columns used:** `turbine_id`, `abnormal_sensor`, `hourly_timestamp`, `state`, `location`

**Goal for the timeline:**
- Show **one line per `state`**.
- X-axis: **`hourly_timestamp`** (hour granularity) for the selected day.
- Y-axis: **OK%** = *count of rows with `abnormal_sensor = 'ok'`* ÷ *total rows* **for that state+hour**.
- Do **not** create separate series for sensor types or statuses—**one series per state only**.
- Include a simple **state multi-select** (all selected by default).

**KPIs:**
- Deduplicate to the **latest record per `turbine_id`** within the day.
- **AUM** = distinct `turbine_id`
- **OK Turbines** = `abnormal_sensor = 'ok'`
- **OK %** = OK / AUM

**Bar chart:**
- From the **deduped** set, **count by `location`** (top 10 + “Other”).

**Simplicity & structure:**
- Keep Streamlit’s built-in multipage setup; only the **Home** page is used here.
- Follow the Cookbook connection method exactly.
