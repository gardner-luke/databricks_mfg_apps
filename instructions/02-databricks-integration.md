# 🔗 Add a Databricks SQL Connectivity Test Page

**Goal:**  
Add a second page **“Connectivity Test”** to the app in **`/field-service-app`** that verifies access to a Unity Catalog table by **following the exact approach in the Apps Cookbook** “Read tables” guide:  
https://apps-cookbook.dev/docs/streamlit/tables/tables_read

**Simplicity Rules:**  
- Keep the code minimal and readable.  
- Use **only** the libraries and connection method recommended in the guide (no substitutions).  
- Assume the **Databricks CLI/profile is already authenticated**; use the same auth context as the guide.

**UI Inputs (required):**  
- **Unity Catalog table** (fully qualified): `catalog.schema.table`  
- **SQL Warehouse ID** (**ID only**; do **not** accept a name)

**Behavior:**  
1. Implement the connection and query exactly as shown in the guide (same client, params, and flow).  
2. Resolve any required values (e.g., `server_hostname`, `http_path`, token) the same way the guide instructs.  
3. Execute:
   ```sql
   SELECT COUNT(*) AS row_count FROM <catalog.schema.table>