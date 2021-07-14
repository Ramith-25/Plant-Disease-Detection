Introduction
Getting affected by a disease is very common in plants due to various factors such as fertilizers, cultural practices followed, environmental conditions, etc. These diseases hurt agricultural yield and eventually the economy based on it. 

Any technique or method to overcome this problem and getting a warning before the plants are infected would aid farmers to efficiently cultivate crops or plants, both qualitatively and quantitatively. Thus, disease detection in plants plays a very important role in agriculture.

About the Project
An application that for farmers to detect the type of plant or crops, detect any kind of diseases in them. The app sends the image of the plant to the server where it is analysed using Machine Learning Model. Once detected, the disease and its solutions are displayed to the user

About the Dataset
The dataset used for this project has been taken from Plant-Village- Dataset which can be found here https://github.com/spMohanty/PlantVillage-Dataset/tree/master/raw/color.
The dataset contains a total of 38 classes of plant disease and 1 class of background images listed below:

Apple Scab
Apple Black Rot
Apple Cedar Rust
Apple healthy
Blueberry healthy
Cherry healthy
Cherry Powdery Mildew
Corn Gray Leaf Spot
Corn Common Rust
Corn healthy
Corn Northern Leaf Blight
Grape Black Rot
Grape Black Measles
Grape Leaf Blight
Grape healthy
Orange Huanglongbing
Peach Bacterial Spot
Peach healthy
Bell Pepper Bacterial Spot
Bell Pepper healthy
Potato Early Blight
Potato healthy
Potato Late Blight
Raspberry healthy
Soybean healthy
Squash Powdery Mildew
Strawberry Healthy
Strawberry Leaf Scorch
Tomato Bacterial Spot
Tomato Early Blight
Tomato Late Blight
Tomato Leaf Mold
Tomato Septoria Leaf Spot
Tomato Two Spotted Spider Mite
Tomato Target Spot
Tomato Mosaic Virus
Tomato Yellow Leaf Curl Virus
Tomato healthy
The dataset consists of about 54,305 images of plant leaves collected under controlled environmental conditions. The plant images span the following 14 species:
Apple, Blueberry, Cherry, Corn, Grape, Orange, Peach, Bell Pepper, Potato, Raspberry, Soybean, Squash, Strawberry, and Tomato.


Steps Involved:
Data Preprocessing

1 ) Load Original Image. A total of 800 images for each class Diseased and Healthy is fed for the machine.

Conversion of image from RGB to BGR. Since Open CV (python library for Image Processing), accepts images in RGB coloring format so it needs to be converted to the original format that is BGR format.

Conversion of image from BGR to HSV. The simple answer is that unlike RGB, HSV separates luma, or the image intensity, from chroma or the color information. This is very useful in many applications. For example, if you want to do histogram equalization of a color image, you probably want to do that only on the intensity component, and leave the color components alone. Otherwise you will get very strange colors. In computer vision you often want to separate color components from intensity for various reasons, such as robustness to lighting changes, or removing shadows. Note, however, that HSV is one of many color spaces that separate color from intensity (See YCbCr, Lab, etc.). HSV is often used simply because the code for converting between RGB and HSV is widely available and can also be easily implemented.

Image Segmentation for extraction of Colors. In order to separate the picture of leaf from the background segmentation has to performed, The color of the leaf is extracted from the image.

Applying Global Feature Descriptor. Global features are extracted from the image using three feature descriptors namely :

• Color : Color Channel Statistics (Mean, Standard Deviation) and Color Histogram

• Shape : Hu Moments, Zernike Moments

• Texture : Haralick Texture, Local Binary Patterns (LBP)

After extracting the feature of images the features are stacked together using numpy function “np.stack”.

According to the images situated in the folder the labels are encoded in numeric format for better understanding of the machine.

The Dataset is splitted into training and testing set with the ratio of 80/20 respectively.

Feature Scaling Feature Scaling is a technique to standardize the independent features present in the data in a fixed range. It is performed during the data pre-processing to handle highly varying magnitudes or values or units. If feature scaling is not done, then a machine learning algorithm tends to weigh greater values, higher and consider smaller values as the lower values, regardless of the unit of the values.
Here, we have used Min-Max Scaler. This scaling brings the value between 0 and 1.

Saving the Features. After features are extracted from the images they are saved in HDF5 file. The Hierarchical Data Format version 5 (HDF5), is an open source file format that supports large, complex, heterogeneous data. HDF5 uses a "file directory" like structure that allows you to organize data within the file in many different structured ways, as you might do with files on your computer.

Modeling The Model is trained over 7 machine learning models named :

• Logistic Regression

• Linear Discriminant Analysis

• K Nearest Neighbours

• Decision Trees

• Random Forest

• Naïve Bayes

• Support Vector Machine

And the model is validated using 10 k fold cross validation technique.

9 ) Prediction The models with best performance is them trained with whole of the dataset and score for testing set is predicted using Predict function.

An accuracy of 97% is achieved using Randomm Forest Classifier.

For Model architecture and Working of it please check this website 


