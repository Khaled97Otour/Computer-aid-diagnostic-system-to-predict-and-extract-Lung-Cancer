# Computer-aid-diagnostic-system-to-predict-and-extract-Lung-Cancer
Detecting lung cancer by building a neural network (CNN) that help to predict whether the image that been given to the network is normal or Abnormal.
Furthermore, extract the Abnormal tumor using image processing Technique (FCM segmentation).
However, other techniques have been used to help the process were (ccl algorithm) and image maskes (to clean the edge and unwanted parts from the thorax).

## Requirements are:

- OpenCV
- numpy
- Keras >= 2
- TensorFlow >= 1.15 (or other backend, not tested, TensorFlow is needed by Keras)


# for the Neural network for predicting Lung Cancer
## I design a CNN model to predict whether the input image normal or Abnormal
- The data has been collected from local hospitals and medical clinic(416 sample)
- The model have only two classes Normal = 0 , Abnormal =1
- The model could not predict more than two classes due to small dataset
## First I have to Create the dataset by the following steps :
1. Creating two list for both the image name and the lebels.
2. I build the dataset using pandas (pd.Series(data=my_img)).
3. By using the image name I could add the path therefor I could read the images.
4. img_preprocess was created to pre process the images by reshape theme and add noise (80 , 80 is the image shape).
5. Converting the two list into Arrays.

## Second I create The CNN model   
- is basic sequential model using Conv2D and Maxpooling2D and fully connected layers.
- I use the Adam compiler to measure the Accuracy and loss.
- For validation I split the data 5 % from the total dataset due to low number of data.
The results were the following:

![download](https://user-images.githubusercontent.com/93203143/182347174-c5153ed3-82a4-430a-a74d-f95a491ad653.png)
![download (1)](https://user-images.githubusercontent.com/93203143/182347192-7e9e04dd-3c3a-4eb5-86cc-d19de38131f8.png)

# Lung Tumor Segmentation

## I use the image processing methods to extract the lung tumor
- First thing was to make sure that the image was at size 512x512 (defualt size from DICOM images).
- per-processing stage was by appling filter for the binery-image ( circle with a diameter 300 pixel).
- TO clear all the unwanted areas we use the ccl method and exract the two largest areas (the lungs).
- Using the biolgical knowladge ( the highest density in the Lung, and the shape as well as the area of the tumor) I was able to use FCM to extract the tumor.
