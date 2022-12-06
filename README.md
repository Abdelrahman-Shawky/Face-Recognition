# Face Recognition
## Colab
https://colab.research.google.com/drive/1gqGo_Vd9RSploGFuzMVvW7LAq9IhxYtl?usp=sharing
## Problem Statement
We intend to perform face recognition. Face recognition means that for a given image you can tell the subject id. 
Our database of subjects has 40 subjects.
## Objectives
### Download the Dataset and Understand the Format
- ORL dataset is available at the following link. https://www.kaggle.com/kasikrit/att-database-of-faces/
- The dataset has 10 images per 40 subjects. Every image is a grayscale image of size 92x112.
### Generate the Data Matrix and the Label vector
- Convert every image into a vector of 10304 values corresponding to the image size.
- Stack the 400 vectors into a single Data Matrix D and generate the label vector y.
The labels are integers from 1:40 corresponding to the subject id.
### Split the Dataset into Training and Test sets
- From the Data Matrix D 400x10304 keep the odd rows for training and the even rows for testing. This will give you 5 instances per person for training and 5 instances per person for testing.
- Split the labels vector accordingly.
### Classification using PCA
- Compute the projection matrix U. Define the alpha = {0.8,0.85,0.9,0.95}
- Project the training set, and test sets separately using the same projection matrix.
- Use a simple classifier (first Nearest Neighbor to determine the class labels).
- Find Accuracy for every value of alpha separately.
### Classification using LDA
- Calculate the mean vector for every class Mu1, Mu2, ..., Mu40.
- Replace B matrix by S<sub>b</sub>.

𝑆<sub>𝑏</sub>=Σ<sub>k=1</sub><sup>m</sup> 𝑛<sub>𝑘</sub>(𝜇<sub>𝑘</sub>−𝜇)(𝜇<sub>𝑘</sub>−𝜇)𝑇
      
Here, m is the number of classes, 𝜇 is the overall sample mean, and 𝑛<sub>𝑘</sub> is the number of samples in the k-th class.
  - S matrix remains the same, but it sums S1, S2, S3, ...S40.
  - Use 39 dominant eigenvectors instead of just one. You will have a projection matrix U<sub>39x10304</sub>.
- Project the training set, and test sets separately using the same projection matrix U. You will have 39 dimensions in the new space.
- Use a simple classifier (first Nearest Neighbor to determine the class labels).
- Find Accuracy for the Multiclass LDA on the face recognition dataset.
- Compare the results to PCA results.
### Classifier Tuning
- Set the number of neighbors in the K-NN classifier to 1,3,5,7.
- Plot the performance measure (accuracy) against the K value. This is to be done for PCA and LDA.
### Comapre vs Non-Face Images
- Download non-face images and make them of the same size 92x112. and try to solve the classification problem of faces vs. Non-faces.
  - Show failure and success cases.
  - Show how many dominant eigenvectors will you use for the LDA solution
  - Plot the accuracy vs the number of non-face images while fixing the number of face images.
  - Criticize the accuracy measure for large numbers of non-face images in the training data.
