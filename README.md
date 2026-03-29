# Tree Segmentation and DBH Estimation from LiDAR Data

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Viggo-Troback/Tree-segmentation-and-DBH-estimation-from-lidar-data/blob/main/tree_segmentation.ipynb)

A lightweight Python pipeline for individual tree segmentation and trunk diameter estimation from LiDAR point clouds (.las/.laz), developed as a faster alternative to the industry-standard `lidR` package in R for use on low-powered hardware.

---

## Features

- Read and preprocess `.las` / `.laz` point clouds
- Filter by classification (ground, vegetation, etc.)
- Treetop detection using adaptive local maximum filter
- Tree instance segmentation using K-Means with treetop-guided initialization
- Crown area estimation via convex hull
- Maximum inscribed circle estimation per crown
- DBH (Diameter at Breast Height) estimation using allometric scaling
- 2D and 3D visualizations with optional overlays

---

## Requirements

Install dependencies with:

```bash
pip install -r requirements.txt
```

Or in Google Colab, run the first cell of the notebook which handles installation automatically.

---

## Usage

1. Open the notebook in Colab or Jupyter
2. Upload your `.las` / `.laz` file or use the provided example data in `/data`
3. Set your parameters (species, tree count, height threshold, DBH threshold)
4. Run all cells

---

## Parameters

| Parameter | Description | Default |
|---|---|---|
| `min_height` | Minimum point height to consider as vegetation | `2.0` m |
| `top_percentile` | Top fraction of points used for treetop detection | `0.90` |
| `species` | Tree species for allometric DBH estimation | `Norway Spruce` |
| `threshold` | DBH threshold for marking large trees | `15` cm |

---

## Supported Species (DBH Estimation)

Allometric coefficients from Petersson & Ståhl (2006) and Näslund (1947):

- Norway Spruce (*Picea abies*)
- Scots Pine (*Pinus sylvestris*)
- Birch (*Betula spp.*)

---

## Limitations

- Segmentation accuracy decreases in densely clustered canopies
- DBH estimation is approximate and species-dependent
- Designed for already height-normalised point clouds

---

## References

- Petersson, H. & Ståhl, G. (2006). Functions for below-ground biomass of Pinus sylvestris, Picea abies, Betula pendula and Betula pubescens in Sweden. *Scandinavian Journal of Forest Research*
- Näslund, M. (1947). Functions and tables for computing the cubic volume of standing trees. *National Institute for Forestry Research*
- [lidRtutorial by Tristan Goodbody](https://github.com/tgoodbody/lidRtutorial)

---

## License

MIT
