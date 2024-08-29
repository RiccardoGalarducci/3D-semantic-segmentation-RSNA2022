
<p align="center">
  <img height="250" width="250" src="https://github.com/RiccardoGalarducci/3D-semantic-segmentation-RSNA2022-kaggle/blob/main/images/thumbnail.png" hspace="40">
  <img height="250" width="250" src="https://github.com/RiccardoGalarducci/3D-semantic-segmentation-RSNA2022-kaggle/blob/main/images/site-logo.svg">
</p>


# 3D Semantic Segmentation - RSNA 2022

The **[RSNA 2022 Cervical Spine Fracture Detection](https://www.kaggle.com/competitions/rsna-2022-cervical-spine-fracture-detection)** is organized by the Radiological Socity of North America (RSNA) along with the American Society of Neuroradiology (ASNR) and the American Society of Spine Radiology (ASSR).
The ultimate goal of the challenge is to develop an AI system used to aid in the detection and localization of cervical spine fractures.

The training dataset provided is constituted by 2019 CT scans, with one folder for each scan, containing image data in dicom file format. Moreover, segmentation masks (pixel level annotations) are provided for a subset (87 scans) of the training set. The pixels assume values of 1 to 7 for C1 to C7 (seven cervical vertebrae) and 8 to 19 for T1 to T12. This data is provided in the nifti file format. 

This repository contains the first task of the RSNA 2022 challenge, i.e., develop a 3D semantic segmentation model to assign segmentation masks to the unlabelled CT scans in the training data.

## Description

The project consists in four main steps which are briefly summarized below

### 1. Data Preparation
   The data preparation phase includes multiple transformations performed over the CT scans and the segmentation masks. We resize CT scans, which differs in length, to a **target spatial size** ensuring that all inputs to the model have the same dimensions. In addition, we scale the intensity of each volume. We exploit many image augmentation techniques.
   For what concern the multi-class segmentation masks we apply **binary one-hot encoding**.
### 2. Model Implementation 
The 3D segmentation model has **UNet** architecture which is state-of-the-art for 3D segmentation of medical images. We exploit **[MONAI](https://monai.io/)**  library for its implementation. 
### 3. Model Training
The model has been trained using **AdamW** optimizer with learning rate scheduler. The loss function employed is the weighted sum of **Dice Loss** and **BCE (Binary Cross Entropy) Loss**.

```math
\text{Loss} = \alpha \cdot \text{BCE} + \beta \cdot \text{Dice Loss}
```

The model has been trained for 320 epochs. 

<p align="center">
  <img width="45%" src=https://github.com/user-attachments/assets/84658b27-d0bd-415d-bedb-b34b6d8e758e hspace="40">
  <img width="45%" src=https://github.com/user-attachments/assets/25cb8924-3e8e-4315-9516-aa9fb544e205>
</p>


### 4. Prediction


## Repository Overview


## Collaborators

* **[Cosimo Faeti](https://github.com/CosimoFaeti)**
