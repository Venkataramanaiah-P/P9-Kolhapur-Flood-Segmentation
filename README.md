# P9: Kolhapur Flood Segmentation — U-Net Deep Learning

## Overview
End-to-end deep learning pipeline for flood detection 
using satellite imagery over Kolhapur district, 
Maharashtra, India.

## Study Area
Kolhapur district, Maharashtra — one of India's most 
flood-prone regions. P7 identified 225,646 people at 
flood risk using GIS weighted overlay analysis.

## Technical Stack
| Component | Technology |
|-----------|-----------|
| Model | U-Net |
| Encoder | EfficientNet-B0 (ImageNet pretrained) |
| Framework | PyTorch + segmentation-models-pytorch |
| Satellite Data | Landsat-8 Collection 2 (30m, 4 bands) |
| Loss Function | BCE + Dice (class imbalance handling) |
| Environment | Google Colab T4 GPU |

## Workflow
1. Sentinel-2 + Landsat-8 data acquisition via GEE
2. Flood mask resampling (30m alignment)
3. Training chip generation (130 chips, 256x256)
4. Transfer learning from ImageNet weights
5. Training with BCE + Dice combined loss
6. Evaluation: IoU, F1, Precision, Recall

## Results
| Metric | Value |
|--------|-------|
| Best IoU | 0.048 |
| Best F1 | 0.092 |
| Training chips | 130 |
| Flood class % | 5.5% |
| Epochs | 50 |

## Key Findings
- **Data quality > model architecture**
- Flood risk zones ≠ flood water extent masks
- 130 chips insufficient for deep learning
- Temporal matching between image and mask is critical
- Class imbalance (5.5% flood) requires weighted loss

## Limitations & Next Steps
- Current mask = risk zones (DEM + rainfall + NDVI)
- Need: SAR-derived flood extent for actual water pixels
- Need: 500+ chips for better generalization
- Next: Sentinel-1 SAR flood extent retraining

## Project Progression
| Project | Description |
|---------|-------------|
| P7 | Kolhapur Flood Hazard Map — QGIS weighted overlay |
| P8 | P7 rebuilt in ArcGIS Pro — Python Map Algebra |
| P9 | U-Net deep learning segmentation (this project) |
| P10 | MAHSR corridor change detection (coming) |

## Files
- `GeoAi_v_0_0_004.ipynb` — complete pipeline notebook

## Author
**Venkataramanaiah Poliboyina (Raman)**  
Survey Manager, L&T MAHSR Bullet Train Project  
GitHub: github.com/Venkataramanaiah-P  
LinkedIn: linkedin.com/in/venkataramanaiahpoliboyina