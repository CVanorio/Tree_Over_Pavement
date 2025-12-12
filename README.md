# Tree_Over_Pavement  
## Identifying Tree Canopy Over Paved Surfaces Using NAIP Imagery and Deep Learning

## Summary

This project develops and evaluates a workflow for detecting **tree canopy that overhangs paved surfaces (tree over pavement, TOP)** using high-resolution NAIP imagery and a teacher–student U-Net segmentation framework. Training labels are generated automatically by intersecting buffered OpenStreetMap pavement features with Meta Global High Resolution Canopy Height Maps, eliminating the need for manual annotation. Models are trained on tiled 224×224 image chips and evaluated using accuracy, IoU, precision, recall, and F1 metrics.

## Research Question

Can a deep learning model reliably distinguish tree canopy that overhangs pavement using only RGB and NIR NAIP imagery at inference?

## Motivation

Tree canopy over pavement influences urban heat, stormwater runoff, and green infrastructure performance, but it is rarely, if ever, mapped because pavement under the canopy is often fully obscured in aerial imagery. Identifying this class is important for urban hydrology, cooling, and GI planning. Automating label generation enables scalable, reproducible mapping across cities without the need for costly manual labeling.

## Dataset

The model-ready dataset used in this project is available [here](https://drive.google.com/drive/folders/1IohJ4p7b2hXmYYkassmejs-5YOzG1LSP?usp=drive_link).


### Dataset Description

The dataset consists of **224×224 pixel image chips** organized into `training`, `validation`, and `testing` splits. Each chip includes:

- **Images (`*_stack.tif`)**  
  A 6-band raster containing:
  - RGB and Near-infrared (NIR) bands, from NAIP 1-m imagery
  - Binary tree canopy mask
  - Binary paved surface mask  


  <img width="781" height="166" alt="image" src="https://github.com/user-attachments/assets/4e557de1-149c-482a-91a9-c12cb48a704d" />
  

- **Labels (`*_label.tif`)**  
  A 3-class mask where:
  - 0 = background  
  - 1 = tree over pavement (TOP)  
  - 2 = tree not over pavement (TNP)
 

<img width="805" height="807" alt="image" src="https://github.com/user-attachments/assets/e5771f5e-1227-47c4-bb97-7f0b3c0dcc07" />


The dataset contains 2536 images total. These are split across three folders: train with 1775 images (70%), val with 380 images (15%), and test with 381 images (15%). The images cover the city of Madison, WI. All 6 bands are used for teacher training, and the first 4 bands (NAIP-only) are used to train the student and baseline models.

## Notes

To run the training and evaluation script:

1. Add a shortcut copy of the dataset folder to your Google Drive by right-clicking the provided folder, selecting organize, and clicking add shortcut.
3. Mount Google Drive in Google Colab and set the local dataset path (e.g., `/content/drive/MyDrive/your_TOP_dataset_copy`).
4. Run the full notebook; all required dependencies are installed automatically.




