
# Pepper-4D 🌱<br>

This repository provides the official dataset release for the paper:<br><br>

**Pepper-4D: A Spatiotemporal 3D Point Cloud Dataset for Pepper Plant Phenotyping**<br>

F. Ahmed†, D. Li†, Z. Wang, S. Jobaer, J. Huang, T. Li, J. Hou, B. Zhao*<br>
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
- **Data modality:** 3D point clouds (XYZ + RGB)
- **Temporal resolution:** Daily or bi-daily scans
- **Acquisition method:** Structure-from-Motion (SfM) + NeRF reconstruction
- **Environment:** Indoor controlled conditions

---

## Dataset Subsets<br>

Pepper-4D consists of three subsets capturing different growth scenarios and
experimental conditions.

### Subset 1 — Full Lifecycle<br>
- **Plants:** 11  
- **Point clouds:** 460  
- **Description:**  
  Long-term monitoring from early vegetative growth to flowering,
  fruiting, and senescence.
- **Annotations provided:**  
  - Organ semantic segmentation  
  - Organ instance segmentation  
  - Temporal organ tracking  
  - Plant health classification  

---

### Subset 2 — Geotropism Experiments<br>
- **Plants:** 8  
- **Point clouds:** 238  
- **Description:**  
  Pepper plants subjected to controlled pot overturning and recovery
  to study geotropism and structural reorientation.
- **Annotations provided:**  
  - New organ detection labels  
  - Geotropism state labels  

---

### Subset 3 — Early–Mid Growth<br>
- **Plants:** 10  
- **Point clouds:** 218  
- **Description:**  
  Early and middle growth stages with rapid organ emergence and canopy expansion.
- **Annotations provided:**  
  - No manual annotations  
- **Intended use:**  
  Unsupervised learning, self-supervised learning, and generative modeling.

---

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
│   │       │   ├── day_000.txt
│   │       │   └── ...
│   │       ├── instance/
│   │       │   ├── day_000.txt
│   │       │   └── ...
│   │       ├── temporal/
│   │       │   ├── day_000.txt
│   │       │   └── ...
│   │       └── health/
│   │           ├── day_000.txt
│   │           └── ...
│   ├── plant_02/
│   │   └── ...
│   └── ...
│
├── subset_2/
│   ├── plant_01/
│   │   ├── frames/
│   │   │   ├── day_000.txt
│   │   │   ├── day_002.txt
│   │   │   └── ...
│   │   └── labels/
│   │       └── new_organs_detection/
│   │           ├── day_000.txt
│   │           └── ...
│   ├── plant_02/
│   │   └── ...
│   └── ...
│
└── subset_3/
    ├── plant_01/
    │   ├── frames/
    │   │   ├── day_000.txt
    │   │   └── ...
    │   └── labels/
    │       └── (no annotations)
    └── ...






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

**Naming convention:**

- `day_xxx` indicates the temporal index of the scan.
- Smaller indices correspond to earlier growth stages.
- Larger indices correspond to later growth stages.

This directory structure is consistent across all subsets of Pepper-4D.

