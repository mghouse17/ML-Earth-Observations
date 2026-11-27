# ML Earth Observations

Hands-on AI and machine learning for Earth observation payloads in ESSE 4360 (Payload Design), York University.

Three notebooks that run in Google Colab (free tier) or on any laptop with Python. Each downloads its own public data.

| Notebook | Data | Models | Time (CPU, defaults) | Open in Colab |
|---|---|---|---|---|
| `01_EuroSAT_RGB_Classifiers.ipynb` | EuroSAT RGB: 27 000 Sentinel-2 tiles, 10 classes (~90 MB) | Logistic regression and random forest on colour features, k-means (no labels), small CNN (~24 k parameters), optional ResNet-18 transfer learning (GPU) | ~10 min | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1SycH2WWsTqBIm9iMnAFGMLydPpH4XzXn?usp=sharing) |
| `02_EuroSAT_Multispectral_Bands.ipynb` | EuroSAT 13-band (~2 GB zip, read without unpacking) | Real spectral signatures, NDVI/NDWI, random forest RGB vs 13 bands with band importance, small CNN on 3 vs 13 bands | ~10 min after download | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1fIIrCxtt4Zjpl6Mr5qhCBhey4bJZQb5h?usp=sharing) |
| `03_Sentinel1_Flood_Mapping_SAR.ipynb` | Sen1Floods11 hand-labelled chips: Sentinel-1 VV/VH, Sentinel-2, water labels (defaults ~100 chips, ~0.5 GB) | Otsu threshold, per-pixel random forest on S1 / S2 / S1+S2, small U-Net (~0.5 M parameters), IoU per flood event | ~15 min | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1145fUZLNmo74ywLtQjLVxsdmCqAfX1V8?usp=sharing) |

## Quick start

1. Click the **Open in Colab** badge for the notebook you want to use.
2. (Optional) Select **Runtime → Change runtime type → T4 GPU** (if available), then save.
3. Select **Runtime → Run all**.

The free Colab tier is enough for these activities; GPU availability and usage limits may vary. A Google account is needed to run notebooks, but no GitHub account is required to open these public notebooks. You only need **Save a copy in Drive** if you want to keep your own changes.

## Data sources
- **EuroSAT:** P. Helber et al., IEEE JSTARS 12(7), 2019; MIT licence. Notebook 1 downloads it with `torchvision.datasets.EuroSAT`; notebook 2 downloads the 13-band archive from the TorchGeo Hugging Face mirror (the same URL TorchGeo uses).
- **Sen1Floods11:** D. Bonafilia et al., CVPR Workshops 2020; public Google Cloud bucket `gs://sen1floods11` (v1.1). Notebook 3 downloads over HTTPS and falls back to `gsutil` if HTTPS fails.

## Testing status
All three notebooks ran start to finish here, but on stand-in data: the real Sen1Floods11 sample chip copied under several names (notebook 3), and random images in the EuroSAT folder and zip layouts (notebooks 1–2). The download URLs come from the current torchvision, TorchGeo and Sen1Floods11 code on GitHub, but this workspace cannot reach those hosts, so **the downloads themselves have not been tested**. Run each notebook once in Colab before class.

## Citation / data credits

- P. Helber et al., "EuroSAT: A Novel Dataset and Deep Learning Benchmark for Land Use and Land Cover Classification," IEEE JSTARS 12(7), 2019 (MIT licence). [Official dataset and licence](https://github.com/phelber/EuroSAT#license).
- D. Bonafilia et al., "Sen1Floods11: A Georeferenced Dataset to Train and Test Deep Learning Flood Algorithms for Sentinel-1," CVPR Workshops 2020. [Paper](https://openaccess.thecvf.com/content_CVPRW_2020/html/w11/Bonafilia_Sen1Floods11_A_Georeferenced_Dataset_to_Train_and_Test_Deep_Learning_CVPRW_2020_paper.html).
