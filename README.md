# Exercise: Mapping Model Explanations
## GeoAI & Geovisualization — Explainability on Maps

**Goal:** train a simple spatial prediction model, extract feature contributions, and render them using four map types, drawn **on a basemap of Salzburg**:
1. Proportional symbol map
2. Choropleth (aggregated) map
3. "Attribution surface" (interpolated heatmap, stand-in for saliency/Grad-CAM)
4. Uncertainty-aware map (confidence encoded alongside the prediction)

**Scenario:** synthetic bike-share demand at 400 locations scattered around Salzburg's city center, predicted from four features: distance to center, 
green-space fraction, population density, and transit access. The demand values, features, and model are entirely synthetic — only the geography (Salzburg).

Notes:
>> This exercise is inspired by recent work on GeoXAI (Geospatial eXplainable AI), which argues that standard XAI outputs — SHAP values, feature attributions — lose their meaning when stripped of geographic context, and need dedicated geovisualization techniques rather than generic plots.

>> Specifically, the four map types built in this notebook (proportional symbols, choropleth aggregation, interpolated surfaces, and confidence-aware maps) follow the visualization concepts proposed for mapping Shapley values in geospatial machine learning:

- Roussel, C. (2024). Visualization of explainable artificial intelligence for GeoAI. Frontiers in Computer Science, 6, 1414923. https://doi.org/10.3389/fcomp.2024.1414923

- Roussel, C., & Böhm, K. (2023). Geospatial XAI: A review. ISPRS International Journal of Geo-Information, 12(9), 355. https://doi.org/10.3390/ijgi12090355

The synthetic Salzburg bike-share scenario, the RandomForest model, and the specific figures in this notebook are original teaching material built for this course — they are not taken from the papers above. The papers are cited because the underlying idea (visualize per-location feature attributions using multiple map types rather than a single generic plot, since geographic aggregation and interpolation change what a viewer perceives) is drawn directly from that line of research.

>> **Internet access is required** for this notebook (tile downloads for the basemap). Run `pip install contextily geopandas` first if these aren't already installed.
>> **Note:** default basemap is Esri World Street Map, which is free and requires no API key.
