# ⚡ Step 6: Connect to Live Data

**Goal:** Replace all mock data with live Databricks queries.

---

**Load configuration from `config.yaml`:**
```python
import yaml
from pathlib import Path

config_path = Path(__file__).parent.parent / "config.yaml"
with open(config_path) as f:
    config = yaml.safe_load(f)

WAREHOUSE_ID = config["warehouse_id"]
CATALOG = config["catalog"]
SCHEMA = config["schema"]
```

Add `pyyaml` to `requirements.txt`.

---

**Tables:**

- `turbines_metadata` — `turbine_id, latitude, longitude, model, status, last_maintenance`
- `turbine_telemetry` — `timestamp, turbine_id, power_output_mw, expected_output_mw, wind_speed_mps, vibration_level`

---

**Create cached query functions with `@st.cache_data(ttl=60)`:**

1. `get_turbines_metadata()` — `SELECT * FROM {CATALOG}.{SCHEMA}.turbines_metadata`

2. `get_telemetry()` — `SELECT timestamp, turbine_id, power_output_mw, expected_output_mw FROM {CATALOG}.{SCHEMA}.turbine_telemetry ORDER BY timestamp`
   - **Important:** Convert timestamp with `df['timestamp'] = pd.to_datetime(df['timestamp'])`

3. `get_kpis()` — Returns dict with:
   - `total_devices` = `COUNT(DISTINCT turbine_id)`
   - `maintenance_required` = `COUNT WHERE status IN ('Error', 'Warning')`
   - `healthy_pct` = `100 * COUNT(status='Active') / total`
   - `current_output` = `SUM` of latest `power_output_mw` per turbine (use `ROW_NUMBER()` window function)

---

**Update Chart:**
- Group telemetry by timestamp, SUM `power_output_mw` and `expected_output_mw`
- **Sort by timestamp** before plotting
- Plot as two lines: Real Output (purple) and Expectation (green dashed)

---

**Update Map:**
- Use `latitude`/`longitude` from metadata
- Color by status: Active=green, Warning=yellow, Error=red

---

**Update GenAI Summary:**
- Pull actual turbine IDs from metadata for error/warning turbines
- Keep static analysis text

---

**Error handling:** Wrap data loading in try/except, show `st.error()` if connection fails.
