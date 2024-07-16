# Objectives of the project:
The main objective of this work is to propose deep learning-based methods for binary image classification (True/Fake) and then to evaluate the performance of these implemented approaches.

# The implemented approaches
In this project we have implemented 3 distinct approaches, each based on a very specific technique:

- Direct approach (CNN)
- Frequency approach (Fourier spectrum)
- Dimensionality reduction approach (Auto-encoder)

# Datasets
We used 5 main datasets to perform this work:

- **For the real images**
  -  The IMDB-WIKI dataset. [Dataset link](https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/static/wiki_crop.tar), [Scientific Paper](https://data.vision.ee.ethz.ch/cvl/rrothe/imdb-wiki/)


- **For the fake datasets**
  - Deep Fake Face (DFF) [Hugging Face](https://huggingface.co/datasets/OpenRL/DeepFakeFace):
    - Inpainting: Inpainting stable diffusion 
    - Text2image: Stable diffusion v1.5
    - Insight: Toolbox InsightFace

  - 140k Real and Fake faces (Available on [Kaggle](https://www.kaggle.com/datasets/xhlulu/140k-real-and-fake-faces))
 
  # Datasets distribution with PCA

  ![PCA data distribution](https://github.com/Malekbennabi3/TER_Notebooks/blob/main/img/Acp.png)
  
  The data were displayed to make sure that the different datasets are interlaced and not linearly separable, in such a way that the model differentiates them by characteristics.

  # Approaches

  - **Direct approach**:
    This approach is based on training a convolutional neural network(CNN) on images from the inpainting and wiki datasets.
    The goal is to build a classifier capable to distinguish between real and faked images.
    To achieve this, we opted for fine-tuning and CNN models based on pre-trained architectures.
    ![Direct approach](https://github.com/Malekbennabi3/TER_Notebooks/blob/main/img/direct.png)
    
  - **Fourier approach**:
    For this approach, we select DenseNet_V2 because of its ability to converge quickly.
    The calculation of the Fourier transform enables us to capture specific features that are often present in deepfakes but invisible in the spatial domain.

    To carry out this method we generated a dataset by following the steps below:
    - Conversion of each image into grey levels
    - Application of the 2D Fourier Transform to the greyscale image
    - Centring the Zero Frequency (for easier viewing)
    - Calculation of the Magnitude Spectrum (Logarithm of the absolute value of the Fourier transform)
    - Recording Magnitude Images: The resulting images of the magnitude spectrum were recorded and used as input data for the DenseNet_V2 model.
     ![Fourier approach](https://github.com/Malekbennabi3/TER_Notebooks/blob/main/img/fourier.png)  

  - **Autoencodeur approach**:
    For this approach, we used an autoencoder trained on 60,000 images from the CelebA dataset.
    The aim was to develop a model capable of producing compact and informative compact and informative embeddings of images of faces, that can be used for binary classification to distinguish real images from deepfakes.
    The autoencoder consists of an encoder and a decoder. The encoder transforms the images into a latent vector, while the the decoder reconstructs the images from this latent vector.

    # Experiments

    - Training (Inpainting Dataset ):
      - train set 80%
      - validation set 10%
      - testing set 10%

    - Evaluation (30k images from each dataset):
      - Dataset Insight
      - Dataset Text2image
      - Dataset 140k images(GAN).
     
    # Results

    - Direct approach:
      ![Direct approach](https://github.com/Malekbennabi3/TER_Notebooks/blob/main/img/res_direct.png)  


    - Fourier approach
      ![Fourier approach](https://github.com/Malekbennabi3/TER_Notebooks/blob/main/img/res_fourier.png)  


    - Autoencoder appraoch
      ![Autoencoder approach](https://github.com/Malekbennabi3/TER_Notebooks/blob/main/img/res_auto.png)  

        

# *for more details and information, please consult the final* [Report [French]](https://github.com/Malekbennabi3/TER_Notebooks/blob/main/Rapport_TER.pdf)
    
  
