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
        -  GAN: Biggan, Gaugan, Stargan
    - Accuracy: 93.99%

    #### Level 3(Diffusion Model) :
    - Accuracy: 85.00%

    #### Level 3(GAN) :
    - Accuracy: 93.50%


- ## MODEL 2
  
    ## Pipeline

    #### Preprocessing
    - Gaussian Blur: 
        - Smooth the images
        - Reduce high-frequency noise.

    - JPEG Compression:
        - Aids in reducing the overall data size
        -  Beneficial for storage and transmission purposes

    #### Encoding the Image
    - Chose the OpenAI CLIP model with the architecture ViT-L/14 for image encoding
    - Transforming the input image into a 768-dimensional feature vector.
    -  Encoded representations generated by CLIP capture semantic information about the content of the images


    ####  Dimensionality Reduction
    - Configured the autoencoder to reduce the dimensionality of the feature space from 768 to 200
    - Captures the most salient aspects of the input images, facilitating faster computations and potentially improving model generalization.

    ####  Classification
    - Employed the 200-dimensional image vectors obtained through the autoencoder dimensionality reduction as input for the image classification task.
    - Utilized a variety of machine learning algorithms for classification, including Nearest Neighbours, SVM decision tree.

    [![App Screenshot](https://drive.google.com/uc?id=1KE6mpSnRcyEQU4WUZpx2nzgdTMDqowWr)](https://drive.google.com/file/d/1KE6mpSnRcyEQU4WUZpx2nzgdTMDqowWr/preview)


    ## Results
    - #### Decision Tree Classifier
        - Accuracy: 0.7250
        - Precision: 0.6945
        - Recall: 0.8033
        - F1 Score: 0.7450
    - #### Nearest Neighbours
        - Accuracy: 0.8283
        - Precision: 0.8031
        - Recall: 0.8700
        - F1 Score: 0.8352
    - #### Support Vector Classification
        - Accuracy: 0.7150
        - Precision: 0.6748
        - Recall: 0.8300
        - F1 Score: 0.7444

