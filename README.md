## Aircraft-Detection-in-Satellite-Imagery
GA Capstone Project

### Background
The aim of this project is to help address the difficult task of detecting the location of airplanes in satellite images. Automating this process can be applied to many issues including monitoring airports for activity and traffic patterns, and defense intelligence. 

### Problem Statement
Civil aviation authorities and airport operators need a way to improve air traffic management, safety and capacity monitoring capabilities. Similarly, space management of aircraft storage sites like the one in Alice Springs (where SIA and Scoot parked their aircraft during the COVID-19 pandemic) can be a challenge as well.

### The Project
Build an object detection model that can accurately identify and locate aircraft within satellite images, achieving at least 0.75 mAP.

### Data
The Airbus Aircraft Dataset contains 103 satellite images with corresponding annotations for each target airplane. These are sample images from the Airbus OneAtlas platform.

### Models
2 Models (YOLOv7 and YOLOv8) are fine-tuned on the Airbus Aircraft Dataset for use in the satellite imagery detection task.

### Target Metric
Mean Average Precision (mAP)  
The mAP incorporates the trade-off between precision and recall and considers both false positives (FP) and false negatives (FN). An aircraft detection system would need to balance recall with precision to ensure that capacity is correctly monitored. The presence of too many false detections (whether positive or negative) would be highly detrimental to efficiency and the effectiveness of the model.

### Limitations:
1. Access.  
This model was trained on a sample dataset from Airbus OneAtlas with a resolution of 2560x2560. Full resolution of satellite images from Airbus' OneAtlas Pleaides is 40,00 x 40,000. Due to the size of the targets, higher resolution images for training are likely to result in even better performance.
2. Time.  
Hyperparameter tuning was mostly left to the training scripts and functions.  
Given more time, the dataset can be used to train other model architecture for better performance comparison.

Future Directions
1. It would be great to have images across a greater variety of backgrounds, e.g. over water, to train and test on. This will help us in improving the model such that it is able to help with surveillance of oceanic flights and possibly be used in search and rescue. 
2. Expand dataset to include aircraft that are not commercial jets. Classification of aircraft into military, civilian. Or even finer grained subcategories would no doubt prove to be useful to a wider range of stakeholders. 
3. Experiment with the use of synthetic training data.
4. Deploy the model on a platform such as UP42 that is able to provide "live" satellite feeds.

Credits:  
The Airbus Aircraft Detection Dataset a is licensed under the Creative Commons BY-NC-SA 4.0 International license:
https://creativecommons.org/licenses/by-nc-sa/4.0/ and was obtained from https://www.kaggle.com/datasets/airbusgeo/airbus-aircrafts-sample-dataset
