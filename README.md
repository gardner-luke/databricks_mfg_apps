# Databricks Manufacturing Apps

A collection of instructions and reference examples for building Streamlit-based manufacturing and field service applications on the Databricks Apps platform.

## Overview

This repository provides step-by-step guides and proven patterns for developing data-driven Streamlit applications that integrate with Databricks Unity Catalog and SQL Warehouses. The instructions follow a progressive approach, starting with a bare-bones application and gradually adding connectivity, live metrics, and advanced features.

## Repository Structure

```
databricks_mfg_apps/
├── examples/              # Reference applications (READ-ONLY)
│   └── streamlit-data-app/
│       ├── app.py
│       ├── app.yaml
│       └── requirements.txt
└── instructions/          # Step-by-step development guides
    ├── 01-base-app.md
    ├── 02-databricks-integration.md
    └── 03-live-metrics.md
```

## Instruction Guides

### 01. Base App
Build a minimal, single-page Streamlit app designed for Databricks Apps deployment:
- Simple navigation using Streamlit's built-in multipage system
- Mock KPIs and synthetic data visualizations
- Essential file structure (`app.py`, `requirements.txt`, `app.yaml`)

### 02. Databricks Integration
Add connectivity testing capabilities:
- Unity Catalog table access
- SQL Warehouse connection testing
- Authentication using Databricks SDK

### 03. Live Metrics
Implement real-time data visualization:
- Dynamic KPIs from Unity Catalog tables
- Time-series analysis with state-based filtering
- Location-based aggregations and charts

## Technologies Used

- **Streamlit**: Modern Python web framework for data applications
- **Databricks Apps**: Deployment platform for data-driven applications
- **Databricks SDK**: Python SDK for Databricks services
- **Databricks SQL Connector**: SQL interface to Databricks compute resources
- **Unity Catalog**: Unified governance solution for data and AI assets

## Getting Started

1. **Review the examples folder** to understand proven patterns and structures
   - ⚠️ The examples folder is read-only for reference purposes only

2. **Follow the instruction guides sequentially**:
   - Start with `instructions/01-base-app.md`
   - Progress through each guide as you build features
   - Each guide builds upon the previous one

3. **Set up your development environment**:
   ```bash
   pip install streamlit databricks-sdk databricks-sql-connector
   ```

4. **Configure Databricks authentication** using the Databricks CLI or environment variables

## Development Principles

- **Simplicity-first**: Build minimally, add features incrementally
- **Mock data initially**: Use synthetic data before connecting to live sources
- **Follow patterns**: Reference examples for proven approaches
- **No premature abstraction**: Keep code readable and straightforward

## Resources

- [Databricks Apps Cookbook](https://apps-cookbook.dev/)
- [Streamlit Documentation](https://docs.streamlit.io/)
- [Databricks App Templates](https://github.com/databricks/app-templates)

## License

This project is intended for internal use and development guidance.

