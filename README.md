# DeepFake-Image-Detection

In response to the rising concerns surrounding the malicious use of generative AI, particularly in the creation of deepfakes, our project aims to develop novel and robust approaches for detecting and mitigating the spread of misinformation. Focusing on cross-data and cross-domain generalization in detection methods, the goal is to develop adaptive algorithms capable of real-time identification of manipulated content, thereby minimizing the dissemination of misinformation. Overcoming challenges associated with diverse datasets and evolving generative AI techniques, the project aims to enhance the adaptability and transparency of deepfake detection models. 

We have created two models for the task:

- ## MODEL 1

## Approach

#### Level 1 - Real vs. AI Detection:
- Objective: Distinguish real data from AI-generated content.
- Implementation: Use ResNET-50 as Image encoder.
- Fully connected layer added, with output size equal to two at this level, followed by a SoftMax activation.

#### Level 2 - GAN vs. DM Discrimination:
- Objective: Differentiate between images generated by GANs and DMs.
- Implementation: Again Use ResNET-50 as Image encoder.
- Fully connected layer added, with output size equal to two at this level, followed by a SoftMax activation.


#### Level 3 - Specific Architecture Recognition:
- Task: Identify the specific architecture within the dataset.
- Divided into two sub-modules:
    1. "Level 3-GANs": Creating 3-classes classifier using ResNET-50 as backbone for image encoding.
    2. "Level 3-DMs": Similarly creating 
## Pipeline

[![App Screenshot](https://drive.google.com/uc?id=1JghafLAkzn1omzVsunzSPXZ1OOgmMmAw)](https://drive.google.com/file/d/1JghafLAkzn1omzVsunzSPXZ1OOgmMmAw/preview)


## Results

#### Level 1 :
- Training data: Laion(Real) and Dalle(Fake)
- Testing data: Laion(Real) and Biggan(Fake)
- Accuracy: 76.96%

#### Level 2 :
- Training data:
    - Diffusion Model: Dalle, Glide, LDM
    - GAN: Biggan, Gaugan, Stargan
- Accuracy: 93.99%

#### Level 3(Diffusion Model) :
- Accuracy: 85.00%

#### Level 3(GAN) :
- Accuracy: 93.50%


#### MODEL 2
- Pixel space is inadequate for classification as it lacks meaningful information beyond point-to-point pixel correspondences, necessitating mapping images into a feature space.
- To get the features we use  CLIP:ViT-L/14, trained on 400M image-text pairs, meeting the requirements of exposure to diverse images and capturing low-level details.
- Then employing simple classification methods utilizing for real/fake classification on the basis of features extracted from CLIP model.
