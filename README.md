# Attention-based CNN for Small Object Classification
(published ... ➡️ Paper Link)

## 📚 Overview
We propose an Attention-based CNN (A-CNN) model that addresses the challenges of small object classification in real-world manufacturing environments. Unlike traditional CNNs that struggle with object-to-image area ratio (OAR) constraints, our model leverages an  attention mechanism to dynamically focus on small objects, achieving superior classification accuracy and efficiency.

Key innovations of our model include:

- Integration of a spatial transformer module to adaptively extract Regions of Interest (ROI), increasing OAR without manual preprocessing.
- A multi-task learning framework that enables end-to-end training with minimal data labeling (only 5% of the dataset labeled), significantly reducing human effort and time.
- For an edge device, NVIDIA Jetson Nano, providing real-time inference (33 fps) while maintaining high accuracy (99.92%).
  
These contributions ensure that our A-CNN is not only effective but also practical for deployment in resource-constrained environments, such as automated optical inspection (AOI) systems.

## 📂 Architecture of the Attention-based CNN model
This model utilizes a spatial transformer (Attention) module to sample the ROIs from the input images. The localization network predicts the center coordinates of the ROIs, and the classification network assigns class scores based on the ROIs. In the Attention module, the sizes of both the ROI and the resized ROI are hyperparameters.
<p align="center"> <img src="https://github.com/user-attachments/assets/92532d03-2370-4742-80a9-56b42642bc15" alt="A-CNN Architecture" width="80%"> </p>


## Dataset
This dataset was created as part of our research. It is publicly available to facilitate reproducibility and further advancements in the field.

- **Images**:
  - `train data`: from device 0 
  - `test/`: from device 1
- **Labels**:
  - YOLO format labels corresponding to each image.    
<p align="center"> <img src="https://github.com/user-attachments/assets/330c10ba-4341-4730-98d3-066826c86074" alt="Dataset Example" width="80%"> </p>


## 📝 Citation
If you use this dataset, please cite the following paper:

@article{Kim2024,
  title={An Attention-based CNN Model for Small Object Classification in Automated Optical Inspection Systems},
  author={Kim, Hyun-Yong and Lee, Hong-ki},
  journal={IEEE Transactions on Instrumentation and Measurement},
  year={2024},
  volume={XX},
  number={X},
  pages={XXX-XXX},
  doi={10.xxxx/yourpaperdoi}
}
