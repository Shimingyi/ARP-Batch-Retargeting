# ARP-Batch-Retargeting

A common issue with kinematic motion resources is the variability in skeleton configurations among different datasets, including but not limited to SMPL, Mixamo, Vicon, and Human3.6M. However, to train a large-scale animation framework for consistent character rigging, all motion data must be retargeted onto a unified skeleton. Given the vast number of motion data, manually performing this retargeting process within software presents annoying stuff.

In this repository, I shared my personal pipeline designed for the batch retargeting of BVH files. This pipeline employs purely kinematic operations without relying on fitting techniques. It includes:
- A script for Blender that enables the use of ARP (Auto-Rig-Pro) in batch mode.
- A multi-step post-processing with Python to enhance the quality of the retargeted motion.

Additionally, I provided two examples, along with all necessary configuration files, derived from previous works: [CAMDM](https://github.com/AIGAnimation/CAMDM/tree/main) and EfficiantPhaseMP(Coming very soon). These samples demonstrate the process of converting motion data with 100STYLE_to_Mixamo and SMPL_to_Mixamo, showcasing the practical application of the proposed pipeline. 

As a reference, converting the AMASS dataset, which includes over 14k BVH files, takes approximately 30 minutes for the entire process.

### Updates
06/17/2024: Repo init. 
