# DeepFake-Image-Detection

In response to the rising concerns surrounding the malicious use of generative AI, particularly in the creation of deepfakes, our project aims to develop novel and robust approaches for detecting and mitigating the spread of misinformation. Focusing on cross-data and cross-domain generalization in detection methods, the goal is to develop adaptive algorithms capable of real-time identification of manipulated content, thereby minimizing the dissemination of misinformation. Overcoming challenges associated with diverse datasets and evolving generative AI techniques, the project aims to enhance the adaptability and transparency of deepfake detection models. 

We have created two models for the task:

#### MODEL 1
- The model includes a multi-level hierarchical approach using ResNET models for classification.
- This approach includes three levels of classification:
      - 1. Real vs. AI-generated images
      - 2. GANs vs. DMs
      - 3. Recognition of specific GAN/DM architectures

#### MODEL 2
- Pixel space is inadequate for classification as it lacks meaningful information beyond point-to-point pixel correspondences, necessitating mapping images into a feature space.
- To get the features we use  CLIP:ViT-L/14, trained on 400M image-text pairs, meeting the requirements of exposure to diverse images and capturing low-level details.
- Then employing simple classification methods utilizing for real/fake classification on the basis of features extracted from CLIP model.
