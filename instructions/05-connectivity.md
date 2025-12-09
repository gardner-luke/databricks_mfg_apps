# 🔗 Step 5: Databricks Connection Test

**Goal:** Add a connection test section at the bottom of the dashboard.

**Add to bottom of `app.py`:**

- Divider and header: "🔗 Databricks Connection Test"
- Text input for Warehouse ID (default from config.yaml)
- Text input for table name (default from config.yaml)
- "Test Connection" button

**Connection pattern:**

```python
from databricks.sdk.core import Config
from databricks import sql

cfg = Config()
http_path = f"/sql/1.0/warehouses/{warehouse_id}"
with sql.connect(
    server_hostname=cfg.host,
    http_path=http_path,
    credentials_provider=lambda: cfg.authenticate
) as connection:
    with connection.cursor() as cursor:
        cursor.execute(f"SELECT COUNT(*) as row_count FROM {table_name}")
        result = cursor.fetchall_arrow().to_pandas()
```

**On click:** Show spinner, then green success with row count or red error message.
