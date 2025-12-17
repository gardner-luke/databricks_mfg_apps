# Databricks Manufacturing Apps - Vibe Coding Template

A template framework for building Streamlit applications on Databricks Apps using AI-assisted development with structured prompts.

## 🤔 What is This?

This is a **vibe coding template** that demonstrates how to use structured prompts with AI coding assistants (like Cursor) to rapidly build data-driven Streamlit applications. The `instructions/` folder contains carefully crafted prompts that guide AI to build a complete wind farm monitoring dashboard incrementally.

## 📁 Repository Structure

```
databricks_mfg_apps/
├── config.yaml              # Databricks connection settings (catalog, schema, warehouse)
├── setup_data.py            # Script to deploy data using config.yaml
├── fsa_env_setup/           # Databricks Asset Bundle for data setup
│   ├── data/                # Sample CSV files (turbine metadata & telemetry)
│   ├── src/                 # Notebooks (load_data.py)
│   └── resources/           # Job definitions
└── instructions/            # Vibe coding prompts for AI assistants
    ├── 01-app-setup.md      # Create basic Streamlit app structure
    ├── 02-kpi-cards.md      # Add KPI metric cards
    ├── 03-power-chart.md    # Add power output chart
    ├── 04-summary-map.md    # Add GenAI summary & turbine map
    ├── 05-connectivity.md   # Add Databricks connection testing
    └── 06-live-data.md      # Connect to live Databricks data
```

## 🚀 How to Use

### 0. Prerequisites

Before you begin, ensure you have the following:

1. **Databricks CLI installed and authenticated**:
   - Follow the [official tutorial](https://docs.databricks.com/aws/en/dev-tools/cli/tutorial) to install and set up the Databricks CLI.
   - **Note:** Ensure your CLI is correctly authenticated (`databricks auth login`) and targeted to your workspace.
2. **Databricks Permissions**:
   - Access to an existing **Catalog** (or permission to create one).
   - Access to a **Schema** (or permission to create one).
   - A **SQL Warehouse** available for use (you will need its ID).

### 1. Configure Environment

Edit `config.yaml` with your Databricks settings:

```yaml
catalog: "CATALOG_NAME"
schema: "SCHEMA_NAME"
warehouse_id: "WAREHOUSE_ID"
```

### 2. Set Up Data

Run the setup script to deploy the sample data to your Databricks environment:

```bash
python setup_data.py
```

This script reads your configuration and runs the Databricks Asset Bundle to create tables. **Once the script completes successfully and you see the data in your catalog, you are ready to proceed to the next step.**

### 3. Build the App with AI

Use the **Cursor Agent** to build the application. In the Chat window, ensure you are using the "Agent" mode (or "Composer" with Agent capabilities) so it can execute terminal commands and create files.

**How to "Tag" Files:**
To provide instructions to the AI, type `@` followed by the filename (e.g., `@01-app-setup.md`) in the chat input. This gives the AI the specific context it needs for that step. You may also drag and drop the files from your explorer into the Cursor Chat window.

Run the following prompts sequentially in the Agent chat:

**1. Initialize the App:**

```bash
@instructions/01-app-setup.md    # Creates wind-farm-app/ with basic structure
```

**✨ Verify it works:**
After this first step is complete, you can start the app to see your progress:

```bash
cd wind-farm-app
pip install -r requirements.txt
streamlit run app.py
```

*Tip: Keep the app running in your terminal. As you apply the next steps, just refresh your browser to see the changes.*

**2. Add Features:**

```bash
@instructions/02-kpi-cards.md    # Adds 4 KPI metric cards
@instructions/03-power-chart.md  # Adds power output line chart
@instructions/04-summary-map.md  # Adds GenAI summary panel & map
@instructions/05-connectivity.md # Adds Databricks connection testing
@instructions/06-live-data.md    # Replaces mock data with live queries
```

Each prompt builds on the previous one, progressively adding features to the dashboard.

## 🏗️ What Gets Built

Following all 6 instruction prompts creates a **wind-farm-app/** directory containing a Streamlit dashboard for "Cool Electric Co." with:

| Step | Feature | Description |
|------|---------|-------------|
| 01 | App Setup | Basic Streamlit app with header and deployment config |
| 02 | KPI Cards | 4 metric cards (devices, maintenance, health %, output) |
| 03 | Power Chart | Plotly line chart showing real vs expected power output |
| 04 | GenAI Summary & Map | AI insights panel + interactive turbine location map |
| 05 | Connection Test | Databricks SQL Warehouse connectivity verification |
| 06 | Live Data | All components connected to Unity Catalog tables |

## 🛠️ Technologies

- **Streamlit** - Python web framework for the dashboard
- **Databricks Apps** - Deployment platform
- **Databricks SDK & SQL Connector** - Data access
- **Unity Catalog** - Data governance
- **Plotly** - Interactive visualizations
- **Databricks Asset Bundles** - Infrastructure as code for data setup

## 💡 Philosophy

This template follows vibe coding principles:
- **Simplicity-first** - Build minimally, add incrementally
- **Progressive complexity** - Each step builds on the previous
- **Clear instructions** - Specific and actionable prompts
- **AI-friendly** - Optimized for AI assistant interpretation

## 📚 Resources

- [Databricks Apps Cookbook](https://apps-cookbook.dev/)
- [Streamlit Documentation](https://docs.streamlit.io/)
- [Databricks App Templates](https://github.com/databricks/app-templates)

## 📄 License

Use as a starting point for your own projects. Adapt freely.
