
<p align="center">
  <img src="figures/graphical_abstract.jpg" width="95%">
</p>


<h1 align="center">Pepper-4D </h1>
<p align="center"><i>  </i></p>

F. Ahmed†, D. Li†, Z. Wang, S. Jobaer, J. Huang, T. Li, J. Hou, B. Zhao<br>
<ins>†</ins> *Equal contribution*<br>
<ins>*</ins> *Corresponding author*<br><br>

(To be published)<br>
[[Paper](TO_BE_UPDATED)]<br><br>

---

## Table of Contents
- [Introduction](#introduction)
- [Dataset Overview](#dataset-overview)
- [Comparison with Existing 3D Crop Datasets](#comparison-with-existing-3d-crop-datasets)
- [Dataset Acquisition and Reconstruction](#dataset-acquisition-and-reconstruction)
- [Dataset Subsets](#dataset-subsets)
- [Tasks and Results](#tasks-and-results)
- [Dataset Structure](#dataset-structure)
- [Supported Tasks](#supported-tasks)
- [Data Download](#data-download)
- [Citation](#citation)

---


## Introduction<br>

Three-dimensional (3D) plant phenotyping plays a crucial role in analyzing
plant structure, organ-level traits, and growth dynamics.
While recent advances in 2D and 3D vision have accelerated research in plant
phenotyping, publicly available **spatiotemporal 3D datasets for pepper plants**
remain extremely limited.

Pepper-4D addresses this gap by providing a **comprehensive 4D (3D + time) point
cloud dataset** capturing the complete growth and developmental process of
pepper plants under controlled indoor conditions.
The dataset enables detailed analysis of plant structure, organ dynamics,
temporal growth patterns, and plant health status.
Pepper-4D is designed as a benchmark resource for both discriminative and
generative learning methods on 3D plant point clouds.

---

## Cultivation and Data Collection Conditions

All subsets were collected under the same controlled indoor cultivation conditions:
- **Lighting:** indoor lights, ~12 h/day
- **Temperature:** ~25 °C (average)
- **Relative humidity:** ~45% (average)
- **Growing medium:** standard soil in pots
- **Nutrients:** no additional nutrients applied
- **Irrigation:** consistent routine across plants (see paper for details)

**Scanning schedule:** Point clouds were scheduled at ~2-day intervals **after plants reached a minimum size suitable for reliable 3D scanning**.  
The month ranges (e.g., July–December) denote the overall cultivation period; not every plant was scanned at every scheduled timepoint, resulting in unequal sequence lengths.

---

The Pepper-4D dataset comprises three distinct subsets that collectively capture developmental diversity and experimental variability in pepper plants cultivated under controlled indoor conditions. Indoor lighting was provided for approximately 12 h per day, with an average ambient temperature of ~25 °C and average relative humidity of ~45%. Point clouds were scheduled to be acquired at two-day intervals once plants reached a minimum size suitable for reliable 3D scanning; the reported month ranges denote the overall cultivation period, and the realized scan times vary across plants (e.g., no scans in the very early seedling stage and occasional missing time points), resulting in unequal sequence lengths. All three subsets were collected under the same indoor cultivation conditions, and representative samples are shown in Fig. 1. Subset 1 (Fig. 1(a)) contains 460 point clouds from 11 potted plant sequences collected during the July–December 2024 cultivation period, covering the full developmental cycle from early vegetative growth to flowering, fruiting, and senescence. Subset 2 (Fig. 1(b)) includes 238 point clouds from 8 plant sequences collected between September and December 2024 for geotropism testing: potted plants were placed on their side (approximately horizontal) for a controlled duration and then restored upright to observe recovery behavior. This subset captures structural reorientation and morphological adaptation under gravitational perturbation. Subset 3 (Fig. 1(c)) consists of 218 point clouds from 10 plant sequences collected during the July–September 2025 cultivation period, focusing on early-to-mid developmental phases characterized by rapid organ emergence and canopy expansion. Together, these subsets span major growth events—including budding, flowering, fruiting, organ disappearance, and withering—making Pepper-4D a comprehensive benchmark for plant-level and organ-level spatiotemporal phenotyping of pepper. <br>

<p align="center">
  <img src="figures/Figure_1.png" width="95%">
</p>

## Dataset Overview<br>

- **Species:** Pepper (*Capsicum annuum*)
- **Total plants:** 29
- **Total point clouds:** 916
- **Total points:** 322.72 million
- **Total dataset size:** ~20 GB
- **Data modality:** 3D point clouds (XYZ)
- **Temporal resolution:** Bi-daily scans
- **Environment:** Indoor controlled conditions


## Comparison with Existing 3D Crop Datasets<br>

The following table provides a high-level comparison between Pepper-4D and
representative publicly available 3D crop datasets.

<table align="center">
  <thead>
    <tr>
      <th align="center">Dataset</th>
      <th align="center">Species</th>
      <th align="center"># Point Clouds</th>
      <th align="center"># Temporal Coverage (4D)</th>
      <th align="center">Acquisition Modality</th>
      <th align="center">Color</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">Conn et al. (2017)</td>
      <td align="center">Tomato, Tobacco, Sorghum</td>
      <td align="center">558</td>
      <td align="center">Yes</td>
      <td align="center">Laser</td>
      <td align="center">No</td>
    </tr>
    <tr>
      <td align="center">ROSE-X (2020)</td>
      <td align="center">Rose</td>
      <td align="center">11</td>
      <td align="center">No</td>
      <td align="center">X-ray CT</td>
      <td align="center">No</td>
    </tr>
    <tr>
      <td align="center">Pheno4D (2021)</td>
      <td align="center">Maize, Tomato</td>
      <td align="center">126</td>
      <td align="center">Yes</td>
      <td align="center">Laser</td>
      <td align="center">No</td>
    </tr>
    <tr>
      <td align="center">Soybean-MVS (2023)</td>
      <td align="center">Soybean</td>
      <td align="center">102</td>
      <td align="center">Yes</td>
      <td align="center">MVS</td>
      <td align="center">Yes</td>
    </tr>
    <tr>
      <td align="center">PLANesT-3D (2024)</td>
      <td align="center">Pepper, Rose, Ribes</td>
      <td align="center">34</td>
      <td align="center">No</td>
      <td align="center">SfM-MVS</td>
      <td align="center">Yes</td>
    </tr>
    <tr>
      <td align="center">BonnBeetClouds3D (2024)</td>
      <td align="center">Sugar Beet</td>
      <td align="center">3000</td>
      <td align="center">No</td>
      <td align="center">UAV Photogrammetry</td>
      <td align="center">Yes</td>
    </tr>
    <tr>
      <td align="center">Crops3D (2024)</td>
      <td align="center">Multiple species</td>
      <td align="center">1230</td>
      <td align="center">Partial</td>
      <td align="center">SfM-MVS, TLS</td>
      <td align="center">Yes</td>
    </tr>
    <tr>
      <td align="center">MaizeField3D (2025)</td>
      <td align="center">Maize</td>
      <td align="center">1045</td>
      <td align="center">No</td>
      <td align="center">TLS + Procedural</td>
      <td align="center">Yes</td>
    </tr>
    <tr>
      <td align="center"><b>Pepper-4D (2026)</b></td>
      <td align="center"><b>Pepper</b></td>
      <td align="center"><b>916</b></td>
      <td align="center"><b>Yes</b></td>
      <td align="center"><b>SfM + NeRF</b></td>
      <td align="center"><b>Yes</b></td>
    </tr>
  </tbody>
</table>



---

## Dataset Acquisition and Reconstruction<br>

<p align="center">
  <img src="figures/data_acquisition_pipeline.jpg" width="95%">
</p>

Pepper-4D was constructed through a multi-stage pipeline including image
acquisition, preprocessing, 3D reconstruction, and plant-only point cloud
generation. Multi-view images were captured for each plant at each time step,
followed by 3D reconstruction and post-processing to obtain temporally aligned
point clouds.

---

## Dataset Subsets<br>

Pepper-4D consists of three subsets capturing different growth scenarios and
phenotyping tasks.

### Subset 1 — Full Lifecycle<br>

<p align="center">
  <img src="figures/subset1_lifecycle.jpg" width="95%">
</p>

- **Plants:** 11  
- **Point clouds:** 460  
- **Description:**  
  Long-term monitoring from early vegetative growth to flowering,
  fruiting, and senescence.
- **Annotations:**  

  <p align="center">
  <img src="figures/Subset_1.png" width="95%">
</p

---

### Subset 2 — Geotropism Tests <br>

<p align="center">
  <img src="figures/subset2_new_organs.jpg" width="95%">
</p>

- **Plants:** 8  
- **Point clouds:** 238  
- **Description:**  
  Sequences focusing on **new organ detection and Geotropism tests**.
- **Annotations:**  

<p align="center">
  <img src="figures/Subset_2.png" width="95%">
</p
---

### Subset 3 — Early–Mid Growth<br>

- **Plants:** 10  
- **Point clouds:** 218  
- **Description:**  
  Early and mid growth stages with rapid structural changes.
- **Annotations:**  

  <p align="center">
  <img src="figures/Subset_3.png" width="95%">
</p

---


## Tasks and Results <br>

---

### Reproducibility and Baselines

We provide experimental notes and baseline resources used in the manuscript to facilitate reproduction.

Reference implementations:
- PointNet/PointNet++: https://github.com/yanx27/Pointnet_Pointnet2_pytorch
- DGCNN: https://github.com/WangYueFt/dgcnn
- PlantNet/PSegNet: https://github.com/Huang2002200/PlantNet-and-PSegNet
- 3D New-Organ Detection: https://github.com/zingersu/3D-New-Organ-Detection-in-Plant-Growth-from-Spatiotemporal-Point-Clouds
- TrackPlant3D: https://github.com/entarot/TrackPlant3D-3D-organ-growth-tracking-framework-for-organ-level-dynamic-phenotyping

---

### Health assessment by classification

<p align="center">
  <img src="figures/health_classification.jpg" width="95%">
</p>

### Organ Semantic Segmentation 

<p align="center">
  <img src="figures/semantic.jpg" width="95%">
</p>

### Organ Instance Segmentation 

<p align="center">
  <img src="figures/instance.jpg" width="95%">
</p>

### New Organ Detection

<p align="center">
  <img src="figures/new_organ_detection.jpg" width="95%">
</p>

### Organ tracking 

<p align="center">
  <img src="figures/temporal.jpg" width="95%">
</p>

### Generating natural and vivid 3D plants

<p align="center">
  <img src="figures/GAN.jpg" width="95%">
</p>


## Dataset Structure<br>

Each plant sequence follows the same directory structure:

```text
Pepper-4D/
├── subset_1/
│   ├── plant_01/
│   │   ├── frames/
│   │   │   ├── day_000.txt
│   │   │   ├── day_002.txt
│   │   │   └── ...
│   │   └── labels/
│   │       ├── semantic/
│   │       ├── instance/
│   │       ├── temporal/
│   │       └── health/
│   └── ...
│
├── subset_2/
│   ├── plant_01/
│   │   ├── frames/
│   │   └── labels/
│   │       └── new_organs_detection/
│   └── ...
│
└── subset_3/
    ├── plant_01/
    │   ├── frames/
    │   └── labels/
    │       └── (no annotations)
    └── ...

```



**Folder description:**

- `frames/`  
  Contains time-ordered 3D point clouds of the same plant.
  Each file corresponds to one temporal scan and is stored in plain text
  format (`.txt`) with XYZ coordinates (and optional additional attributes).

- `labels/`  
  Contains annotations aligned with each corresponding frame.
  Label files share the same base filename as the frame
  (e.g., `day_002.txt` in `frames/` ↔ `day_002.txt` in `labels/`).

- `semantic/`  
  Point-wise semantic segmentation labels (e.g., stem, leaf).

- `instance/`  
  Point-wise instance segmentation labels, where each unique integer
  corresponds to an individual leaf.

- `temporal/`  
  Point-wise temporal tracking labels, where the same ID across frames
  denotes the same physical organ over time.

- `health/`  
  Frame-level plant health labels (`normal` or `withering`).

- `new_organs_detection/`  
  Detection of new plant organs on crop point clouds is a task focusing on identifying emergent budding/new leaves in the 3D growth sequence.

  

## Supported Tasks<br>

Pepper-4D supports the following research tasks:

- Plant health classification  
- Organ semantic segmentation  
- Organ instance segmentation  
- Organ growth tracking  
- New organ detection  
- Spatiotemporal plant phenotyping  
- 3D plant generation   

---

## Data Download<br>

Due to the large size of the dataset (~20 GB), Pepper-4D is hosted externally.

**Download link:**  
👉 **TO_BE_UPDATED (Google Drive / OneDrive)**


---


## Citation<br>

If you use Pepper-4D in your research, please cite our paper:

```bibtex
@article{pepper4d,
  title   = {Pepper-4D},
  author  = {Ahmed, Foysal and others},
  journal = {To be updated},
  year    = {2026}
}


