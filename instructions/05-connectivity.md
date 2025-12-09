# 🔗 Step 5: Databricks Connection Test

**Goal:** Add a connection test section at the bottom of the main dashboard.

**Reference:** [Databricks Apps Cookbook - Read a Delta table](https://apps-cookbook.dev/docs/streamlit/tables/tables_read)

**Load configuration from `config.yaml`:**

At the top of `app.py`, load the config file from the parent directory:
```python
import yaml
from pathlib import Path

config_path = Path(__file__).parent.parent / "config.yaml"
if config_path.exists():
    with open(config_path) as f:
        app_config = yaml.safe_load(f)
else:
    app_config = {}
```

Add `pyyaml` to `requirements.txt`.

**Add to bottom of `app.py`:**

Add a divider and connection test section with:
- Section header: "🔗 Databricks Connection Test"
- Text input for HTTP Path - **default value loaded from config** (`/sql/1.0/warehouses/{warehouse_id}`)
- Text input for table name - **default value loaded from config** (`{catalog}.{schema}.{tables.metadata}`)
- "Test Connection" button

Both fields should be pre-populated from `config.yaml` but remain editable in the UI.

**Connection pattern** (from Databricks Apps Cookbook):

```python
from databricks.sdk.core import Config
from databricks import sql

cfg = Config()
with sql.connect(
    server_hostname=cfg.host,
    http_path=http_path,
    credentials_provider=lambda: cfg.authenticate
) as connection:
    with connection.cursor() as cursor:
        cursor.execute(f"SELECT COUNT(*) as row_count FROM {table_name}")
        result = cursor.fetchall_arrow().to_pandas()
```

**On click behavior:**
- Validate HTTP path is provided
- Show spinner while connecting
- On success: display green success message with row count
- On error: display red error message

**Expected Result:** A connection test section at the bottom of the dashboard that verifies Databricks SQL connectivity, with fields pre-populated from `config.yaml`.
