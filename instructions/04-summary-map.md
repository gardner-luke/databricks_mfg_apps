# 🗺️ Step 4: GenAI Summary & Map

**Goal:** Add the GenAI Summary panel and turbine map.

**GenAI Summary Panel (left column, above the chart):**

Use `st.container(border=True)` with individual `st.markdown()` calls for each line (do NOT use nested HTML - it won't render correctly).

- Orange "✨ GenAI Summary" header (use inline HTML only for the header styling)
- **Power output analysis** section label (bold)
- ⚡ "Drop in overall output from 21:00 (last night) to now"
- 📈 "Power output is stable at ~75 MW post-drop."
- **Turbine analysis** section label (bold)
- 🔴 "A1234 shut off at 21:00"
- 🟡 "C7890 requires verification of binding device"

**Map of Turbines (full width, below the two-column section):**

Use `st.map()` or Plotly with these turbine locations near Nantucket:

| Turbine | Latitude | Longitude | Marker |
|---------|----------|-----------|--------|
| A1234 | 41.3135 | -70.1088 | Red (error) |
| B5678 | 41.2674 | -70.0907 | Green (active) |
| C7890 | 41.3214 | -70.0976 | Yellow (warning) |

**Expected Result:** A two-column layout with GenAI insights on the left, chart on the right, and a map below showing turbine locations.

