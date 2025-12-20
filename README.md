# Pepper-4D 🌱<br>
*A Spatiotemporal 3D Point Cloud Dataset for Pepper Plant Phenotyping*

<p align="center">
  <img src="figures/graphical_abstract.jpg" width="95%">
</p>

This repository provides the official dataset release for the paper:<br><br>

**Pepper-4D: A Spatiotemporal 3D Point Cloud Dataset for Pepper Plant Phenotyping**<br>

F. Ahmed†, D. Li†, Z. Wang, S. Jobaer, J. Huang, T. Li, J. Hou, B. Zhao<br>
<ins>†</ins> *Equal contribution*<br>
<ins>*</ins> *Corresponding author*<br><br>

(To be published)<br>
[[Paper](TO_BE_UPDATED)]<br><br>

---

## Introduction<br>

Three-dimensional (3D) plant phenotyping plays a crucial role in analyzing
plant structure, organ-level traits, and growth dynamics.
While recent advances in 2D and 3D vision have accelerated research in plant
phenotyping, publicly available **spatiotemporal 3D datasets for pepper plants**
remain extremely limited.

Pepper-4D addresses this gap by providing a **large-scale 4D (3D + time) point
cloud dataset** capturing the complete growth and developmental process of
pepper plants under controlled indoor conditions.
The dataset enables detailed analysis of plant structure, organ dynamics,
temporal growth patterns, and plant health status.
Pepper-4D is designed as a benchmark resource for both discriminative and
generative learning methods on 3D plant point clouds.

---

## Dataset Overview<br>

- **Species:** Pepper (*Capsicum annuum*)
- **Total plants:** 29
- **Total point clouds:** 916
- **Total dataset size:** ~20 GB
- **Data modality:** 3D point clouds (XYZ)
- **Temporal resolution:** Bi-daily scans
- **Environment:** Indoor controlled conditions

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
  Semantic, instance, temporal, and health labels.

---

### Subset 2 — New Organ Emergence<br>

<p align="center">
  <img src="figures/subset2_new_organs.jpg" width="95%">
</p>

- **Plants:** 8  
- **Point clouds:** 238  
- **Description:**  
  Sequences focusing on **new organ emergence and development**.
- **Annotations:**  
  New organ detection labels.

---

### Subset 3 — Early–Mid Growth<br>

- **Plants:** 10  
- **Point clouds:** 218  
- **Description:**  
  Early and mid growth stages with rapid structural changes.
- **Annotations:**  
  None (intended for unsupervised and generative tasks).

---

## Tasks and Results <br>



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
- 3D plant generation and data augmentation  

---

## Data Download<br>

Due to the large size of the dataset (~20 GB), Pepper-4D is hosted externally.

**Download link:**  
👉 **TO_BE_UPDATED (Google Drive / OneDrive)**

Please keep the original directory structure after downloading.

---


## Citation<br>

If you use Pepper-4D in your research, please cite our paper:

```bibtex
@article{pepper4d,
  title   = {Pepper-4D: A Spatiotemporal 3D Point Cloud Dataset for Pepper Plant Phenotyping},
  author  = {Ahmed, Foysal and others},
  journal = {To be updated},
  year    = {2025}
}

---

