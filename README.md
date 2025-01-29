# CBIR
This repo aims to build models that can work in the encrypted domain i.e. understanding the encrypted images without decrypting them.

To this aim two papers were replicated 
The first one : [Secure Similar Image Matching (SESIM): An Improved Privacy Preserving Image Retrieval Protocol over Encrypted Cloud Database](https://ieeexplore.ieee.org/document/9522057) tries to understand encrypted images taking advantage of the homomorphic encryption as the basic arithmitc can be done without decryption. The paper suggest their own encryption method and intorduce a new similarity measure and compare the results with tradional methods with high level feature extracted from the images using vgg-16 and low-level features extracted using HOG. Unfortunately, the results were not replicated.

The second paper is [Privacy-Preserving Image Retrieval Based on Disordered Local Histograms and Vision Transformer in Cloud Computing](https://www.researchgate.net/publication/374101009_Privacy-Preserving_Image_Retrieval_Based_on_Disordered_Local_Histograms_and_Vision_Transformer_in_Cloud_Computing) Where the encryption process takes a simpler approach from the precouis one as it does the following 
1. The image is divided into m x m blocks
2. The blocks are shuffled
3. The pixels within the blocks are shuffled
4. The colors are encoded according to certain equations
5. A vision transformer is trained to extract the features from the images 


The repo consists of 6 notebooks 

1. `CBIR_Proof_of_Concept.ipynb` : The replication of the first paper in which the results were not reproduce 
2. `data_building.ipynb` : This notebook collects the data from three different datasets on kaggle and from every dataset and collect 1000, 100 and 100 samples for training validation and testing sets respectively. **Note:** This notebook was built quickly so you'd have to change the file types for every dataset
3. `model_building.ipynb`: builds on the data of the prevouis notebook and fine-tunes a VGG-16 and ViT on plain text image and on encrypted images to see which model does better
4. `testing.ipynb`: Analyzes the results of the models that were trained in the prevouis notebook and calculates the essential metrics
5. `quantization.ipynb`: Quantizes the model with the best results (VGG16) but just numerically i.e. just changes the range of the weights as the other benfits of quantizing a model can be calculated
6. `cbir_model_testing.ipynb`: Further tests the model to check its results if the number of blocks at inference time were changed from the number of blocks at training time. It also tests how the model would perform if only half of the image was given in addition to testing the addition of random noise
