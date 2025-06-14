# Virtual-Try-On-For-Clothing

## Overview
Virtual Try-On (VTO) technology allows customers to visualize how clothing items will look on them without physically trying them on. This project leverages computer vision, deep learning, and augmented reality to create a realistic and interactive experience for virtual clothing fitting. The project explores and implements state-of-the-art models such as **VITON**, **DeepVTO**, and **ACGPN** to enhance the VTON experience.

![image](https://github.com/user-attachments/assets/4ce2791d-28d0-4f36-9727-0cbc2c55a6d0)


## Available Models for Virtual Try-On

### 1. IDM VTON (Virtual Try-On Network)
[IDM VTON  on Hugging Face](https://huggingface.co/yisol/IDM-VTON)

IDM VTON is a pioneering model in the VTO space. It consists of a two-stage framework:
- **Stage 1**: Generates a coarse synthesized image of the person wearing the target clothes.
- **Stage 2**: Refines the image by enhancing details and correcting errors.

**Strengths**:
- Produces realistic results.
- Can handle various poses and clothing types.
  
## Results of the Pretrained Model:
![image](https://github.com/user-attachments/assets/fa7ebf05-62ee-4642-9aea-012e985ed55c)


### 2. DeepVTO
[DeepVTO on Hugging Face](https://huggingface.co/gouthaml/raos-virtual-try-on-model)

DeepVTO leverages deep learning techniques like Stable Diffusion, DreamBooth, and EfficientNetB3 CNN for feature extraction. It uses OpenPose for estimating person keypoints to accurately position clothing on the user.

**Key Components**:
- **Stable Diffusion & DreamBooth**: Used for high-quality image generation and personalization.
- **EfficientNetB3 CNN**: Captures detailed features from input images.
- **OpenPose**: Estimates human body keypoints to ensure accurate clothing placement.

### 3. ACGPN (Adaptive Content Generative Prior Network)
[ACGPN on GitHub](https://github.com/minar09/ACGPN)

ACGPN incorporates an adaptive content generator and prior network to improve clothing alignment and appearance on the target person.

**Strengths**:
- High-quality results with fine-grained details.
- Effective for a wide range of clothing styles.

![image](https://github.com/user-attachments/assets/74357fef-cab9-40c8-9e76-2c987e8ac7cb)


## Approach to Developing a VTO System

### 1. Data Collection and Preprocessing
- **Dataset**: Collect images of clothing items and human models in various poses.
- **Annotation**: Annotate the dataset with key points, segmentation masks, and clothing categories.
- **Preprocessing**: Normalize and preprocess images for consistent model input.

### 2. Model Training
- **Train the ACGPN model**: Using annotated datasets, train the clothing segmentation network, adaptive content generator, and prior network.
- **Loss Functions**: Utilize loss functions such as L1 loss, perceptual loss, and adversarial loss.

### 3. Deployment
- **API Development**: Develop APIs to integrate the VTO system with front-end applications.
- **User Interface**: Design an intuitive interface for users to upload images and try on clothing.
- **Performance Optimization**: Optimize the system for real-time performance across various devices.

### 4. Testing and Feedback
- **User Testing**: Conduct testing to gather feedback on the system's usability and accuracy.
- **Iterative Improvement**: Make improvements based on user feedback.

## Getting Started with IDM-VTON

### Step 1: Clone the Repository

First, clone the IDM-VTON repository to your local machine using Git:

git clone https://github.com/yisol/IDM-VTON


### Step 2: Install Requirements

Python==3.10.0

#### Install the required packages using pip:

- pip install torch==2.0.1+cu118 torchvision==0.15.2+cu118 torchaudio==2.0.2+cu118 -f https://download.pytorch.org/whl/torch_stable.html

- pip install pytorch-triton

- pip install accelerate==0.25.0 torchmetrics==1.2.1 tqdm==4.66.1 transformers==4.36.2 diffusers==0.25.0 einops==0.7.0 bitsandbytes==0.39.0 scipy==1.11.1 opencv-python gradio==4.24.0 fvcore cloudpickle omegaconf pycocotools basicsr av onnxruntime==1.16.2

- python.exe -m pip install --upgrade pip


### Step 4: Download Checkpoints

Download the necessary checkpoints for IDM-VTON:

1. DensePose Checkpoints: [Download Link](https://huggingface.co/yisol/IDM-VTON/tree/main/densepose)
2. Human Parsing Checkpoints: [Download Link](https://huggingface.co/levihsu/OOTDiffusion/tree/main/checkpoints/humanparsing)
3. OpenPose Checkpoints: [Download Link](https://huggingface.co/lllyasviel/ControlNet/blob/main/annotator/ckpts/body_pose_model.pth)

Place the downloaded checkpoints in the appropriate directories within the IDM-VTON project folder.

### Step 5: Download models
- mkdir yisol
- cd yisol
- git lfs install
- git clone https://huggingface.co/yisol/IDM-VTON

### Step 6: Launch the Gradio UI

Activate your virtual environment and start the Gradio UI to interact with IDM-VTON. Run this in teminal, ensure that you should be inside the directory of IDM-VTON:



- python gradio_demo/app.py

