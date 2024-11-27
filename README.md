# Sensor Fusion for Improved Object Detection in Autonomous Vehicles

## Overview
This project demonstrates a **data-level camera-LiDAR fusion approach** to improve object detection accuracy for autonomous vehicles. It aligns with the Toyota Research Institute's (TRI) mission to advance AI and autonomous vehicle technology. Using the **KITTI dataset**, the project overlays LiDAR point cloud data onto camera images and trains a multimodal deep learning model for object detection.

## Key Features
1. **Sensor Fusion**:
   - Combines **data-level camera and LiDAR inputs** to retain comprehensive spatial and visual information.
2. **Model Architecture**:
   - Utilizes a multimodal deep learning model based on **PointNet** for LiDAR data and a CNN for camera data.
   - Supports multilabel binary classification for 9 object classes.
3. **Dataset**:
   - Employs the **KITTI Object Detection Dataset** with calibration data for precise alignment of camera and LiDAR inputs.
4. **Performance Metrics**:
   - Achieves 86% object detection accuracy using fused data, comparable to LiDAR-only performance.
5. **Data Processing**:
   - Includes point cloud voxelization, normalization, and subsampling to manage GPU constraints.

## Dataset and Preprocessing
- **Dataset (70GB)**: [KITTI Object Detection Dataset](http://www.cvlibs.net/datasets/kitti/)
- **Preprocessing Steps**:
  1. Extracted and visualized LiDAR point clouds and corresponding camera images.
  2. Used calibration matrices to align LiDAR data with camera frames.
  3. Subsampled LiDAR point clouds to 10,000 points to optimize training performance.
  4. Voxelized and normalized LiDAR data to create meaningful 3D representations.

## Model Architecture
### Multimodal Model
- **LiDAR Branch**: Based on **PointNet**, processes 3D point clouds for object detection.
- **Camera Branch**: CNN processes 2D camera images.
- **Fusion Layer**: Concatenates feature outputs from both branches and applies additional dense layers for final classification.

### LiDAR-Only Model
- A standalone **PointNet** implementation for comparison.
- Employs voxelized LiDAR data for optimized object detection.

## Object Detection Classes
- Classes detected: `Car`, `Cyclist`, `Person_sitting`, `Van`, `Pedestrian`, `Misc`, `DontCare`, `Truck`, `Tram`

## Results
- **Multimodal Fusion**:
  - Accuracy: **86%**
  - Strengths: Retains both distance (LiDAR) and texture (camera) data.
  - Challenges: Underfitting likely due to computational constraints which limit model complexity.
- **LiDAR-Only Model**:
  - Accuracy: **~86%**
  - Strengths: Consistent training and inference results.
  - Insights: Simplified representations (e.g., voxelized inputs) may be more effective under resource constraints.

## Key Insights
- Feature-level fusion could outperform data-level fusion due to the reduced complexity and focused representation of input data.
- A more robust model (e.g., **PointNet++**) and larger training datasets could improve the performance of data-level fusion.
- Future work could involve testing various fusion strategies to determine optimal configurations for object detection in autonomous vehicles.

## Prerequisites
- Python 3.7+
- Libraries: `TensorFlow`, `NumPy`, `OpenCV`, `Matplotlib`, `scikit-learn`

Install dependencies:
```bash pip install tensorflow numpy opencv-python matplotlib scikit-learn```

Then run the jupyter notebook.
