# Attention-based CNN for Small Object Classification
* Published in IEEE Transactions on Instrumentation and Measurement on March 5th, 2025.*  
➡️ **[Read the Paper via IEEE](https://doi.org/10.1109/TIM.2025.3548240)**
➡️ <a href="https://drive.google.com/file/d/1Sd6pG3sAqparhOF8mNqujJR55c9HIqKY/view?usp=sharing" target="_blank">Download the paper(pdf)</a>


## 📚 Overview
We propose an Attention-based CNN (A-CNN) model that addresses the challenges of small object classification in real-world manufacturing environments. Unlike traditional CNNs that struggle with object-to-image area ratio (OAR) constraints, our model leverages an  attention mechanism to dynamically focus on small objects, achieving superior classification accuracy and efficiency.

Key innovations of our model include:

- Integration of an Attention module to adaptively extract Regions of Interest (ROI), increasing OAR without manual preprocessing.
- A multi-task learning framework that enables end-to-end training with minimal data labeling (only 5% of the dataset labeled), significantly reducing human effort and time.
- For an edge device, NVIDIA Jetson Nano, providing real-time inference (67.1 fps) while maintaining high accuracy (99.92%).
  
These contributions ensure that our A-CNN is not only effective but also practical for deployment in resource-constrained environments, such as automated optical inspection (AOI) systems.


## 📂 Architecture of the Attention-based CNN model
This model utilizes a spatial transformer (Attention) module to sample the ROIs from the input images. The localization network predicts the center coordinates of the ROIs, and the classification network assigns class scores based on the ROIs. In the Attention module, the sizes of both the ROI and the resized ROI are hyperparameters.
<p align="center"> 
  <img src="https://github.com/user-attachments/assets/92532d03-2370-4742-80a9-56b42642bc15" alt="A-CNN Architecture" width="80%"> 
</p>


## Dataset
This dataset was created as part of our research. It is publicly available to facilitate reproducibility and further advancements in the field. <br>
➡️ <a href="https://drive.google.com/file/d/1-mJ-XuLnGw-MKrtD-E1y6Tp2aSlG_G97/view?usp=sharing" target="_blank">download dataset</a>

- **Images**:
  - `train data`: from device 0 
  - `test data`: from device 1
- **Labels**:
  - YOLO format labels corresponding to each image.    
<p align="center"> 
  <img src="https://github.com/user-attachments/assets/330c10ba-4341-4730-98d3-066826c86074" alt="Dataset Example" width="60%"> 
</p>

## Performance (updated after the paper publication)
The A-CNN model can be effectively trained end-to-end with minimal data labeling compared to object detection methods. Experimental results show that the proposed A-CNN model achieves a classification accuracy of **99.92%** and an inference speed of **62.9 fps** on the NVIDIA Jetson Nano platform, outperforming the smallest models of YOLOv5, YOLOv7, YOLOv8, YOLOv9 and YOLOv10, state-of-the-art object detection algorithms, in terms of both accuracy and latency. Notably, our model has 3.8× faster than the fastest YOLO model, underscoring its efficiency in real-time applications. These findings highlight the potential of the A-CNN model as an accurate and practical solution for small object classification.

**Comparison of the A-CNN with YOLO Object Detection Models**

| Model            | Params (M) | FLOPs<sup>f</sup> (G) | Input (resized) | Accuracy (%) | Latency<sup>a</sup> (ms) |
|:----------------:|:------------:|:--------------:|:-----------------:|:--------------:|:----------------:|
| YOLOv5-Nano     | **1.76**   | **1.55** | 640×480 | 99.67 | **61** |     
|                 |            | **0.67** | 416×312 | 97.92 | 61 |
|                 |            | **0.22** | 224×168 | 82.83 | 55 |
| YOLOv7-Tiny     | 6.02       | 4.95     | 640×480 | **99.83** | 135 |
|                 |            | 2.15     | 416×312 | 98.42 | 135 |
|                 |            | 0.69     | 224×168 |**95.33** | 130 |
| YOLOv8-Nano     | 3.01       | 3.01     | 640×480 | 98.95 | 72 |
|                 |            | 1.33     | 416×312 | 95.58 | **44** |
|                 |            | 0.43     | 224×168 | 64.00 | **44** |
| YOLOv9-Tiny     | 2.01       | 2.94     | 640×480 | 99.50 | 112 |
|                 |            |1.28      | 416×312 | 99.08 | 102 |
|                 |            | 0.41     | 224×168 | 77.08 | 95 |
| YOLOv10-Nano    | 2.71       | 3.15     | 640×480 | 99.75 | 84 |
|                 |            |1.36    | 416×312 | 99.33 | 59 |
|                 |            | 0.44     | 224×168 | 75.08 | 57 |
| A-CNN (base)     | 0.71  | 2.22 | 640×480 | 99.75 | **14.9 (6.2)** |
| A-CNN (best)     | 0.70  | 1.00 | 640×480 | 99.82 | 15.5 (6.3) |
| A-CNN (opt)      | 0.68  | 0.38 | 640×480 | **99.92** | 15.9 (6.6) |

**Notes:**
- <sup>f</sup> FLOPs in the forward process of model, excluding the pre- and post-processing for YOLO models.
- <sup>a</sup> End-to-end inference time measured on the **NVIDIA Jetson Nano**, including the pre- and post-processing.  
  Values in parentheses indicate inference time using **TensorRT with FP32 precision**.


## 📄 **Citation**
If you use this dataset, please cite the following paper:

> **Hyun-Yong Kim, Taek-Joon Yi, and Jong-Yun Lee**  
> _An Attention-based Convolutional Neural Network with Spatial Transformer Module for Automated Optical Inspection of Small Objects_  
> IEEE Transactions on Instrumentation and Measurement, 2025.  
> DOI: [10.1109/TIM.2025.3548240](https://doi.org/10.1109/TIM.2025.3548240)
