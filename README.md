## Data Used
- Building footprints from OpenStreetMap
- Height data: Washington LIDAR Portal (2021, King County West, Tiles 111 & 89)

## Method
1. Selected a 1 km buffer around Seattle city center as a sample for easier computation
2. Extracted OSM building footprints within the buffer
3. Loaded DSM and DTM raster files (tiles 111 & 89)
4. Computed normalized DSM (nDSM = DSM - DTM)
5. Filtered nDSM values to remove outliers and nodata
6. Used `zonal_stats` to compute average height per building
7. Estimated number of floors and total floor area
8. Exported result as a GeoPandas-ready GeoJSON

## Output
- `seattle_building_heights_clean.geojson`: contains valid building polygons with `estimated_height`, `estimated_floors`, and `floor_area`
- `seattle_building_heights_clean_latlon.geojson`: for easy visualization
- `preview_map.png`: visual map of estimated building heights

## Notes
- Only two raster tiles were used for sample coverage to avoid excessive compute
- Buildings with extreme or null height values were filtered
- Average floor height assumed to be 3 meters
