🛰️ Change Detection Using Sentinel-1 & Sentinel-2 (SAR + Optical Fusion)

This project performs change detection using multi-temporal Sentinel-1 (SAR) and Sentinel-2 (optical) satellite imagery.
A fused approach is used, combining spectral indices (NDBI) and SAR backscatter change to produce a final binary change map and confidence map.


📌 Features

Extract ROI from GeoJSON

Download & preprocess Sentinel-2 (S2) surface reflectance

Download & preprocess Sentinel-1 (S1) VV GRD

Apply SCL cloud masking for S2

Convert S1 dB to linear and apply Lee speckle filter

Compute Optical Change (NDBI difference)

Compute SAR Change (dB difference)

Fuse both signals into:

fused_mask.tif → final change detection (0/1)

fused_confidence.tif → confidence (0–255)

Export multiple diagnostic maps (RGB, NDBI, SAR change, union, intersection)



project/
│
├── input/
│   └── roi.geojson
│
├── output/
│   ├── pre_rgb.png
│   ├── post_rgb.png
│   ├── optical_mask.png
│   ├── s1_mask.png
│   ├── fused_mask.tif          ← FINAL CHANGE MASK
│   ├── fused_confidence.tif
│   ├── union_mask.png
│   ├── intersect_mask.png
│   └── ...
│
├── src/
│   └── change_detection.ipynb
│
└── README.md

▶️ How to Run the Project
Step 1 — Add ROI

Place your area of interest in:

input/roi.geojson

Step 2 — Run the main script

python scripts/change_detection.py


| File                 | Description                                              |
| -------------------- | -------------------------------------------------------- |
| **fused_mask.tif**   | **FINAL** binary change map (0 = no change, 1 = changed) |
| fused_confidence.tif | Confidence (0–255)                                       |
| optical_mask.png     | Optical-only detected changes                            |
| s1_mask.png          | SAR-only detected changes                                |
| union_mask.png       | Change detected by either SAR or optical                 |
| intersect_mask.png   | Change detected by both SAR **and** optical              |
| pre_rgb.png          | Pre-change RGB rendering                                 |
| post_rgb.png         | Post-change RGB rendering                                |


