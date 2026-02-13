
<p align="center">
  <img src="figures/graphical_abstract.jpg" width="95%">
</p>


<h1 align="center">Pepper-4D: spatiotemporal 3D pepper crop dataset for phenotyping</h1>
<p align="center"><i>  </i></p>

Foysal Ahmed†; Dawei Li†; Boyuan Zhao; Zhanjiang Wang; Jiali Huang; Tingzhicheng Li; Jingjing Huang; Jiahui Hou; Sayed Jobaer; Han Yan*<br>
<ins>†</ins> *Equal contribution*<br>
<ins>*</ins> *Corresponding author*<br><br>


[[Paper](https://www.mdpi.com/2223-7747/15/4/599)]<br><br>

---

## Table of Contents
- [Introduction](#introduction)
- [Cultivation and Data Collection Conditions](#Cultivation-and-Data-Collection-Conditions)
- [Dataset Overview](#dataset-overview)
- [Comparison with Existing 3D Crop Datasets](#comparison-with-existing-3d-crop-datasets)
- [Dataset Acquisition and Reconstruction](#dataset-acquisition-and-reconstruction)
- [Dataset Subsets](#dataset-subsets)
- [Tasks and Results](#tasks-and-results)
- [Dataset Structure](#dataset-structure)
- [Supported Tasks](#supported-tasks)
- [Download links](#Download-links)
- [Citation](#citation)

---


## Introduction<br>

Pepper-4D is an open 4D (spatiotemporal) point-cloud dataset capturing pepper (*Capsicum annuum*) development from early growth to senescence under controlled indoor conditions. With **916** point clouds from **29** plants and rich temporal/organ annotations, it provides a benchmark and practical resource for dynamic plant phenotyping, including health assessment, organ segmentation, new-organ emergence, growth tracking, and 3D virtual plant generation.

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
The month ranges (e.g., July–December) denote the overall cultivation period.



<p align="center">
  <img src="figures/Figure_1.png" width="95%">
</p>

---

## Dataset Overview<br>

- **Species:** Pepper (*Capsicum annuum*)
- **Total plants:** 29
- **Total point clouds:** 916
- **Total points:** 322.72 million
- **Total dataset size:** ~10 GB
- **Data modality:** 3D point clouds (XYZ)
- **Temporal resolution:** intended ~2-day interval after minimum plant size (variable by plant/sequence)
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

Workflow of image acquisition and 3D reconstruction for the Pepper-4D dataset. (a) is the step of image acquisition and preprocessing; (b) shows the 3D reconstruction step using the NeRFacto framework; and (c) shows the preparation step of the plant-only point cloud by pot removal and filtering on the result from Point Cloud Exporter.


- **Neural Radiance Field (NeRF):** https://docs.nerf.studio/

---

## Dataset Subsets<br>

Pepper-4D consists of three subsets capturing different growth scenarios and
phenotyping tasks.

### Subset 1 — Full Lifecycle<br>

<p align="center">
  <img src="figures/subset1_lifecycle.jpg" width="95%">
</p>

Illustration of the annotation on a pepper point cloud sequence of Subset 1 from Pep-per-4D dataset. From top to bottom: row (a) shows the original point clouds reconstructed across a series of consecutive growth stages from the same sequence; (b) shows the manually-annotated organ instance labels (including individual leaf instances and the stem) with different colors; (c) shows manually-annotated organ semantic labels (stem class and leaf class); (d) shows tempo-rally-aligned organ instance indices across time for organ tracking; and (e) shows the plant-level health status labels covering from the normal (green) stages to the withering (yellow) stages. The interval of the data is 2 days.

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
</p

Representative annotation on a pepper point cloud sequence of Subset 2 from Pep-per-4D dataset. Row (a) shows the original point clouds of the pepper sequence, in which the stages containing the geotropism event are labeled as “Geotropism”. Row (b) presents annotations of the organ-level growth event (new organ) using the Backwards & Forward Labelling (BFL) mechanism proposed in [31].


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


## Tasks and Results<br>
---

### Reproducibility and Baselines

We provide experimental notes and baseline resources used in the manuscript to facilitate reproduction. **For preprocessing and data augmentation, we follow the standard settings and routines from the original reference implementations listed below.**

Reference implementations:
- **PointNet/PointNet++:** https://github.com/yanx27/Pointnet_Pointnet2_pytorch
- **DGCNN:** https://github.com/WangYueFt/dgcnn
- **PlantNet/PSegNet:** https://github.com/Huang2002200/PlantNet-and-PSegNet
- **3D-NOD:** https://github.com/zingersu/3D-New-Organ-Detection-in-Plant-Growth-from-Spatiotemporal-Point-Clouds
- **TrackPlant3D:** https://github.com/entarot/TrackPlant3D-3D-organ-growth-tracking-framework-for-organ-level-dynamic-phenotyping
- **TreeGAN (3D generation):** https://github.com/NNU-GISA/TreeGAN
- **WarpingGAN (3D generation):** https://github.com/yztang4/WarpingGAN

---

### Health assessment by classification

<p align="center">
  <img src="figures/health_classification.jpg" width="95%">
</p>

The comparative qualitative results of health assessment on Pepper-4D. This figure illustrates representative examples from the testing set, covering normal and withering pepper plants. The Ground truth (GT) labels are shown on the 1st row; the results of PointNet, Point-Net++, and DGCNN are listed on the 2nd, 3rd, and 4th rows, respectively. The classified normal (healthy) plants are shown in green and the withering (unhealthy) plants are in olive green, respectively. The misclassified plants are highlighted with a dotted red circle. Across all shown samples, PointNet++ has the best prediction results.

### Organ Semantic Segmentation 

<p align="center">
  <img src="figures/semantic.jpg" width="95%">
</p>

The qualitative results of organ semantic segmentation by the two networks on the Pepper-4D dataset. This figure illustrates representative samples from the testing set, covering plants with varying structural complexity and canopy density. The GTs are shown in the first row, while the results of PlantNet and PSegNet are presented in the second and third rows, respectively. Points corresponding to leaves are in pink, and the stem points are in green. We also enlarge several parts for detailed comparison.


### Organ Instance Segmentation 

<p align="center">
  <img src="figures/instance.jpg" width="95%">
</p>

The comparative qualitative results of instance segmentations of the two networks on the Pepper-4D dataset. The GT labels are shown in the first row, while the predictions of PlantNet and PSegNet are displayed in the second and third rows, respectively. Each leaf instance is rendered in a distinct color for visual clarity. Misclassified or incomplete regions are highlighted with red dotted circles.


### New Organ Detection

<p align="center">
  <img src="figures/new_organ_detection.jpg" width="95%">
</p>

Visualization of two testing sequences in Subset 2 of Pepper-4D. Each sequence is testes by 3D-NOD for new organ detection, and the results are contrasted with GTs. For better visual effect, some areas containing small buds and leaves are enlarged. The points of new organs are rendered in purple, and the points of old organs are rendered in green.


### Organ tracking 

<p align="center">
  <img src="figures/temporal.jpg" width="95%">
</p>

Qualitative results of organ tracking on Pepper-4D using the TrackPlant3D framework. The figure presents two representative pepper growth sequences with manually labeled GTs. In each sequence, the 1st row shows the GTs of organ tracking; the 2nd row shows the instance segmentations as the input of TrackPlant3D (please note that the segmented organs are not aligned in the timeline); the 3rd row shows the result of TrackPlant3D. Only two regions are incorrectly tracked as they are highlighted with red dotted circles.


### Generating natural and vivid 3D plants

<p align="center">
  <img src="figures/GAN.jpg" width="95%">
</p>

Qualitative comparison of GAN-based 3D plant generation on the Pepper-4D dataset. The real samples (the 1st row) illustrate the natural structural variability of pepper plants across the Pepper-4D dataset. TreeGAN (the 2nd row) and WarpingGAN (the 3rd row) generate virtual pepper point clouds that capture both similarity to real morphological patterns and diversity across generated instances.


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
│   ├── plant_12/
│   │   ├── frames/
│   │   └── labels/
│   │       └── new_organs_detection/
│   └── ...
│
└── subset_3/
    ├── plant_20/
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


## Download links<br>

The Pepper-4D dataset is released as three subsets:

- **Subset 1:** https://drive.google.com/file/d/1BYQbJAQ2jogPlnH5Y-nNrnuZz1ZdOumB/view?usp=sharing  
- **Subset 2:** https://drive.google.com/file/d/1gH_kwyMJUNAqTAUyXIqp5iiLIrIiss7i/view?usp=sharing
- **Subset 3:** https://drive.google.com/file/d/14fcwI_b69GfUedd8vt1M0_FqQYE52mC2/view?usp=sharing


---


## Citation<br>

If you use Pepper-4D in your research, please cite our paper:

@article{ahmed2026pepper4d,
  title   = {Pepper-4D: Spatiotemporal 3D Pepper Crop Dataset for Phenotyping},
  author  = {Ahmed, Foysal and Li, Dawei and Zhao, Boyuan and Wang, Zhanjiang and Huang, Jiali and Li, Tingzhicheng and Huang, Jingjing and Hou, Jiahui and Jobaer, Sayed and Yan, Han},
  journal = {Plants},
  year    = {2026},
  volume  = {15},
  number  = {4},
  pages   = {599},
  doi     = {10.3390/plants15040599}
}
