# Tree_Over_Pavement

# Identifying Tree Canopy Over Paved Surfaces Using NAIP Imagery and Deep Learning
## Summary

This project develops and evaluates a workflow for detecting tree canopy that overhangs paved surfaces using high-resolution NAIP imagery, OpenStreetMap geometries, canopy height data, and a teacher–student U-Net segmentation model. Labels are generated automatically through buffered OSM pavement footprints intersected with canopy height, allowing training without manual digitization. Models are trained on tiled 224×224 image chips and evaluated using accuracy, IoU, precision, recall, and F1.

## Research Question

Can a deep learning model reliably distinguish tree canopy that overhangs pavement, using only RGB/NIR NAIP imagery at inference time?

## Motivation

Tree canopy over pavement affects urban heat, runoff, and GI performance, but it is rarely mapped because pavement is visually obscured in aerial imagery. Identifying this configuration is important for hydrology, cooling, and GI planning. Automating label generation and model training supports scalable, reproducible mapping across cities.

## Datasets

| Dataset                                | Description                                                          | Link                                                                                                                                                                             |
| -------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **NAIP (USDA)**                        | 1-m four-band imagery (RGB + NIR) used as model input                | [NAIP](https://developers.google.com/earth-engine/datasets/catalog/USDA_NAIP_DOQQ)                         |
| **OpenStreetMap (OSM)**                | Roads, sidewalks, cycleways, parking areas used to build paved masks | [OpenStreetMap (OSM)](https://www.openstreetmap.org)                                                                                                                   |
| **Meta High-Resolution Canopy Height** | 1-m canopy height used to detect tree presence                       | [High Resolution 1m Global Canopy Height Maps]([https://developers.google.com/earth-engine/datasets/catalog/Meta_Highres_Canopy_Height](https://gee-community-catalog.org/projects/meta_trees/#dataset-citation)) |


