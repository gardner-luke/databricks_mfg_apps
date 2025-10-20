# 🧱 Build the Bare-Bones Base App (Streamlit + Databricks Apps)

**Goal**  
Create a minimal, single-page Streamlit app to be deployed via **Databricks Apps**. Keep everything simple.

**Structure & Navigation (Simplicity-First)**  
- Use **Streamlit’s built-in multipage system** (the `pages/` folder) for future pages.  
- **Do not** add any custom sidebar navigation (no radios, page_link, etc.).  
- For now, include **one page only** (`Home`). Add more pages later **only when asked**.  
- Control labels/order using file names (when we add pages later):  
  - `pages/1_🏠_Home.py`  
  - `pages/2_🔗_Connectivity_Test.py` (will be added in the next prompt)

**Page Content (Home)**  
- Tiny **mock KPI strip** with synthetic values (e.g., *Total Orders, Revenue, Uptime*).  
- **One simple trend chart** (line) with synthetic data.  
- No Databricks connections or external services.

**Files to Create in `/field-service-app`**  
- `app.py` — sets global page config (`page_title`, icon, `layout="wide"`) and shows a welcome header.  
- `pages/1_🏠_Home.py` — renders the mock KPIs + one trend chart (synthetic data only).  
- `requirements.txt` — only `streamlit`.  
- `app.yaml` — minimal Databricks Apps manifest.

**Resources**  
- https://apps-cookbook.dev/docs/category/streamlit  
- https://github.com/databricks/app-templates/tree/main/streamlit-data-app

**Deliverable**  
A runnable, **very bare-bones** Streamlit app saved in **`/field-service-app`** with one page (`Home`), using Streamlit’s built-in multipage structure and **no custom navigation**.