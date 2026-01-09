# Recent SLAM Papers and Their Foundations

## Recent SLAM Works (2022-2024)

### Neural and Learning-Based SLAM

**NICE-SLAM (2022)**
- "NICE-SLAM: Neural Implicit Scalable Encoding for SLAM" by Zhu et al. (CVPR 2022)
- Hierarchical scene representation using multi-resolution hash encoding
- Real-time dense SLAM with neural implicit representations

**Point-SLAM (2023)**
- "Point-SLAM: Dense Neural Point Cloud-based SLAM" by Sandström et al. (ICCV 2023)
- Neural point cloud representation for efficient SLAM
- Better scalability than purely implicit methods

**Co-SLAM (2023)**
- "Co-SLAM: Joint Coordinate and Sparse Parametric Encodings for Neural Real-Time SLAM" by Wang et al. (CVPR 2023)
- Hybrid representation combining coordinate and sparse parametric encoding
- Achieves real-time performance with high quality

**ESLAM (2023)**
- "ESLAM: Efficient Dense SLAM System Based on Hybrid Representation of Signed Distance Fields" by Johari et al. (CVPR 2023)
- Efficient hybrid SDF representation
- Fast convergence and memory efficiency

**Vox-Fusion (2022)**
- "Vox-Fusion: Dense Tracking and Mapping with Voxel-based Neural Implicit Representation" by Yang et al. (ISMAR 2022)
- Voxel-based neural implicit representation
- Improved efficiency over pure MLP approaches

**DROID-SLAM (2021)**
- "DROID-SLAM: Deep Visual SLAM for Monocular, Stereo, and RGB-D Cameras" by Teed & Deng (NeurIPS 2021)
- End-to-end learned visual SLAM
- Differentiable optimization with recurrent networks

### LiDAR SLAM

**KISS-ICP (2023)**
- "KISS-ICP: In Defense of Point-to-Point ICP – Simple, Accurate, and Robust Registration If Done the Right Way" by Vizzo et al. (RA-L 2023)
- Simplified but highly effective ICP-based approach
- Outperforms many complex methods with simplicity

**PIN-SLAM (2024)**
- "PIN-SLAM: LiDAR SLAM Using a Point-Based Implicit Neural Representation for Achieving Global Map Consistency" by Pan et al. (TRO 2024)
- Neural implicit representation for LiDAR SLAM
- Achieves global consistency without loop closure

**FAST-LIO2 (2022)**
- "FAST-LIO2: Fast Direct LiDAR-Inertial Odometry" by Xu et al. (TRO 2022)
- Improved version with incremental k-d tree and direct registration
- Computationally efficient for real-time applications

### Multi-Sensor and Multi-Modal SLAM

**ORB-SLAM3 (2021)**
- "ORB-SLAM3: An Accurate Open-Source Library for Visual, Visual-Inertial and Multi-Map SLAM" by Campos et al. (TRO 2021)
- Multi-map capability with map merging
- Supports monocular, stereo, RGB-D, and visual-inertial configurations

**Kimera (2020)**
- "Kimera: an Open-Source Library for Real-Time Metric-Semantic Localization and Mapping" by Rosinol et al. (ICRA 2020)
- Metric-semantic SLAM with 3D scene understanding
- Real-time performance with semantic segmentation

**SplaTAM (2024)**
- "SplaTAM: Splat, Track & Map 3D Gaussians for Dense RGB-D SLAM" by Keetha et al. (CVPR 2024)
- Uses 3D Gaussian Splatting for scene representation
- Dense RGB-D SLAM with high-quality rendering

**Gaussian Splatting SLAM (2024)**
- "Gaussian Splatting SLAM" by Matsuki et al. (CVPR 2024)
- Monocular SLAM using 3D Gaussian Splatting
- Enables photorealistic novel view synthesis

### Semantic and Object-Level SLAM

**Conceptgraph (2024)**
- "ConceptGraphs: Open-Vocabulary 3D Scene Graphs for Perception and Planning" by Gu et al. (ICRA 2024)
- Open-vocabulary 3D scene graphs from multi-view images
- Integrates vision-language models for semantic understanding

**LERF (2023)**
- "LERF: Language Embedded Radiance Fields" by Kerr et al. (ICCV 2023)
- Embeds CLIP features into NeRF for language queries
- Enables natural language 3D scene understanding

**Conceptfusion (2023)**
- "ConceptFusion: Open-set Multimodal 3D Mapping" by Jatavallabhula et al. (RSS 2023)
- Builds 3D maps with pixel-aligned multimodal features
- Supports text, images, audio queries

## Foundational SLAM Papers (Must-Read Prerequisites)

### Classical Visual SLAM

**MonoSLAM (2007)**
- "MonoSLAM: Real-Time Single Camera SLAM" by Davison et al.
- First real-time monocular SLAM system
- Extended Kalman Filter approach

**PTAM (2007)**
- "Parallel Tracking and Mapping for Small AR Workspaces" by Klein & Murray (ISMAR 2007)
- Separated tracking and mapping into parallel threads
- Introduced keyframe-based mapping

**ORB-SLAM (2015)**
- "ORB-SLAM: A Versatile and Accurate Monocular SLAM System" by Mur-Artal et al. (TRO 2015)
- Feature-based SLAM with ORB features
- Robust loop closing and relocalization
- Foundation for ORB-SLAM2 and ORB-SLAM3

**ORB-SLAM2 (2017)**
- "ORB-SLAM2: an Open-Source SLAM System for Monocular, Stereo and RGB-D cameras" by Mur-Artal & Tardós (TRO 2017)
- Extended to stereo and RGB-D
- Industry standard for feature-based SLAM

**LSD-SLAM (2014)**
- "LSD-SLAM: Large-Scale Direct Monocular SLAM" by Engel et al. (ECCV 2014)
- Direct method using photometric error
- Semi-dense mapping approach

**DSO (2018)**
- "Direct Sparse Odometry" by Engel et al. (TPAMI 2018)
- Direct visual odometry with sparse points
- Photometric calibration and windowed optimization

### LiDAR SLAM

**LOAM (2014)**
- "LOAM: Lidar Odometry and Mapping in Real-time" by Zhang & Singh (RSS 2014)
- Separates odometry and mapping with different frequencies
- Foundation for many LiDAR SLAM methods

**LeGO-LOAM (2018)**
- "LeGO-LOAM: Lightweight and Ground-Optimized Lidar Odometry and Mapping on Variable Terrain" by Shan & Englot (IROS 2018)
- Ground optimization and lightweight implementation
- Widely used in robotics community

**LIO-SAM (2020)**
- "LIO-SAM: Tightly-coupled Lidar Inertial Odometry via Smoothing and Mapping" by Shan et al. (IROS 2020)
- Factor graph optimization with LiDAR-IMU fusion
- Loop closure with efficient place recognition

**FAST-LIO (2021)**
- "FAST-LIO: A Fast, Robust LiDAR-inertial Odometry Package by Tightly-Coupled Iterated Kalman Filter" by Xu & Zhang (RA-L 2021)
- Iterated Kalman filter for tight coupling
- Very fast and efficient

### Core Algorithms and Theory

**Structure from Motion (SfM)**
- "Building Rome in a Day" (2009) by Agarwal et al.
- Large-scale 3D reconstruction from photos

**Bundle Adjustment**
- "Bundle Adjustment — A Modern Synthesis" (2000) by Triggs et al.
- Core optimization technique in SLAM

**ICP (Iterative Closest Point)**
- "A Method for Registration of 3-D Shapes" (1992) by Besl & McKay
- Fundamental algorithm for point cloud registration
- "Object Modelling by Registration of Multiple Range Images" (1992) by Chen & Medioni

**Loop Closure Detection**
- "Bags of Binary Words for Fast Place Recognition in Image Sequences" (DBoW2, 2012) by Gálvez-López & Tardós
- Efficient place recognition using ORB features

**Graph Optimization**
- "g2o: A General Framework for Graph Optimization" (2011) by Kümmerle et al. (ICRA 2011)
- Widely used optimization framework
- "iSAM2: Incremental Smoothing and Mapping Using the Bayes Tree" (2012) by Kaess et al.

### Neural Representations (Foundation for Neural SLAM)

**NeRF (2020)**
- "NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis" by Mildenhall et al. (ECCV 2020)
- Neural implicit representation for 3D scenes
- Foundation for many neural SLAM methods

**Instant NGP (2022)**
- "Instant Neural Graphics Primitives with a Multiresolution Hash Encoding" by Müller et al. (SIGGRAPH 2022)
- Fast neural training with hash encoding
- Key technique used in NICE-SLAM and others

**3D Gaussian Splatting (2023)**
- "3D Gaussian Splatting for Real-Time Radiance Field Rendering" by Kerbl et al. (SIGGRAPH 2023)
- Explicit 3D representation with Gaussians
- Foundation for recent Gaussian-based SLAM methods

**iMAP (2021)**
- "iMAP: Implicit Mapping and Positioning in Real-Time" by Sucar et al. (ICCV 2021)
- First to combine neural implicit representations with SLAM
- Pioneered neural SLAM direction

### Deep Learning for SLAM Components

**SuperPoint (2018)**
- "SuperPoint: Self-Supervised Interest Point Detection and Description" by DeTone et al. (CVPR Workshop 2018)
- Learned feature detector and descriptor
- Used in many learning-based SLAM systems

**SuperGlue (2020)**
- "SuperGlue: Learning Feature Matching with Graph Neural Networks" by Sarlin et al. (CVPR 2020)
- Learned feature matching
- Improves robustness in challenging conditions

**RAFT (2020)**
- "RAFT: Recurrent All-Pairs Field Transforms for Optical Flow" by Teed & Deng (ECCV 2020)
- State-of-the-art optical flow
- Used in DROID-SLAM

## Reading Path Recommendation

### For Classical SLAM:
1. **Start with fundamentals**: ICP → Bundle Adjustment → Graph Optimization (g2o/iSAM2)
2. **Visual SLAM basics**: MonoSLAM → PTAM → ORB-SLAM → ORB-SLAM2 → ORB-SLAM3
3. **Direct methods**: LSD-SLAM → DSO
4. **LiDAR SLAM**: LOAM → LeGO-LOAM → LIO-SAM → FAST-LIO → FAST-LIO2

### For Neural SLAM:
1. **Neural representations**: NeRF → Instant NGP
2. **Neural SLAM**: iMAP → NICE-SLAM → Co-SLAM → ESLAM
3. **Gaussian-based**: 3D Gaussian Splatting → SplaTAM → Gaussian Splatting SLAM
4. **Learning-based**: SuperPoint/SuperGlue → RAFT → DROID-SLAM

### For Semantic SLAM:
1. **Classical semantic**: Kimera
2. **Vision-language**: LERF → ConceptFusion → ConceptGraphs

## Key Conferences and Journals for SLAM

- **Conferences**: CVPR, ICCV, ECCV (vision), ICRA, IROS, RSS (robotics), NeurIPS (learning)
- **Journals**: TRO (Transactions on Robotics), RA-L (Robotics and Automation Letters), IJRR, TPAMI

The SLAM field is rapidly evolving, especially with neural representations and vision-language models. Recent trends include combining classical robustness with neural scene representations, open-vocabulary semantic understanding, and real-time photorealistic rendering.
