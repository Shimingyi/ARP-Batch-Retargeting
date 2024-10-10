# ARP-Batch-Retargeting

![demo](https://github.com/user-attachments/assets/dc6aad9b-2d8a-4f66-8260-9741bd52b639)

This repository provides a simple, lightweight BVH motion retarget pipeline using Blender and ARP (Auto-Rig-Pro).

Few examples are provided, along with all necessary configuration files, derived from previous works: [CAMDM](https://github.com/AIGAnimation/CAMDM/tree/main). These samples demonstrate the process of converting motion data with 100STYLE_to_Mixamo and SMPL_to_Mixamo, showcasing the practical application of the proposed pipeline.

## Introduction

A common issue with kinematic motion resources is the variability in skeleton configurations among different datasets, including but not limited to SMPL, Mixamo, Vicon, and Human3.6M. However, to train a large-scale animation framework for consistent character rigging, it's better to retarget all data onto a unified skeleton to reduce the chance of multi-skeleton animation issues. Given the vast number of motion data, manually performing this retargeting process within software presents annoying stuff.

In this repository, I shared my personal pipeline designed for the batch retargeting of BVH files. This pipeline employs purely kinematic operations without relying on fitting techniques. It includes:

- A script for Blender that enables the use of ARP (Auto-Rig-Pro) in batch mode.
- A multi-step post-processing with Python to enhance the quality of the retargeted motion.

## Requirements

- Blender 3.x or 4.x
- Auto-Rig-Pro (ARP) (3.69 in my case)

## Usage

1. Move the bmap configuration files to the Blender addon configuration folder. It locates the following path in my case:

```
    Windows: C:\Users\USERNAME\AppData\Roaming\Blender Foundation\Blender\3.0\config\addons\auto_rig_pro-master\remap_presets
    Mac: /Users/USERNAME/Library/Application Support/Blender/4.1/scripts/addons/auto_rig_pro-master/remap_presets
```

2. Run the example script in Blender.
   - Open Blender, and paste example code in `blender_retargeting.py` into the script editor.
   - Change the folder path around L350~L352 to your own path.
   - Run it. Then you will find the retargeted BVH files in the output folder.

## Q&A

1. How this pipeline works?

   - This pipeline is based the ARP's remap tool, but we hacked the API to enable the batch mode.


2. How to create your own bmap configuration files?

   - The bmap configuration file is used to define the mapping between the source and target skeleton joints.
   - It's created by ARP. You can use the ARP's remap tool to export your own bmap files. (See the ARP tutorial for more details, such as [How to remap a Mixamo animation in Blender using Auto Rig Pro](https://www.youtube.com/watch?v=7UmWrtYMza8)).


3. Retargeting quality

   - The source skeleton will be scaled to match the target skeleton's size. It will ensure won't have any foot sliding issue due to the different bone lengths.
   - Different skeletons may have different initial T-pose, so the manual alignment is important! (See L398~L432 in `blender_retargeting.py`)

4. About the post-processing

   - It will be released soon with SMPL example.

## Acknowledgement

This code is used for the paper CAMDM, please consider citing if you find it useful.

```
@inproceedings{camdm,
  title={Taming Diffusion Probabilistic Models for Character Control},
  author = {Chen, Rui and Shi, Mingyi and Huang, Shaoli and Tan, Ping and Komura, Taku and Chen, Xuelin},
  year = {2024},
  publisher = {Association for Computing Machinery},
  address = {New York, NY, USA},
  url = {https://doi.org/10.1145/3641519.3657440},
  doi = {10.1145/3641519.3657440},
  booktitle = {ACM SIGGRAPH 2024 Conference Papers},
  keywords = {Character control, character animation, diffusion models},
  location = {Denver, CO, USA},
  series = {SIGGRAPH '24}
}
```
