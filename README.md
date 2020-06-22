# ML Face Expressions Recognitions App

This app is builded using an end-to-end user experience with  Google ML Kit APIs and following the new Material for ML design guidelines. We add our model to this apps to recognize facial expressions which are Angry, Disgust, Fear, Happy, Neutral, Sad, and Surprise.

## Steps to run the App
* Clone this repo
```shell
git clone https://github.com/Ayuniarfina/Final-Project-Bangkit---JKT4-B.git
```
* Create a Firebase project in the Firebase console, if you don't already have one
Add a new Android app into your Firebase project with package name com.google.firebase.ml.md
Download the config file (google-services.json) from the new added app and move it into the module folder (i.e. app/)
* Build and run it on an Android device
* To improve or change the apps with your model, you can put it to /app/arc/main/asset

## Model ML
### Dataset Source

* FER13 dataset: https://www.kaggle.com/jonathanoheix/face-expression-recognition-dataset

### Baseline Model
* File: baselinemodel.ipynb
* Model used whole data from FER13 dataset, which consists of 7 facial expression: Angry, Disgust, Fear, Happy, Neutral, Sad, Surprise
* Architecture used is simple 3 pairs layer of Conv2D(3,3) and MaxPooling2D(2,2)

### Improved Model
* File: improvedmodel.ipynb
* Neutral expression dropped to reduce ambiguitiy. There're 6 facial expressions (Ekman, 1977)
* Transfer learning used InceptionV3 model, trained on imagenet. Fine tuning at 200 last layers.

### Scenarios Done
1. Using cleaned dataset. FER13 cleaned:https://www.kaggle.com/gauravsharma99/fer13-cleaned-dataset
  - Result: higher acc but not enough classes (5 classes only)
2. Using combined dataset between cleaned FER13 and original FER13 dataset
  - Result: lower acc than original FER13 dataset caused by smaller dataset
3. Reduced FER13 dataset
  - Best result at 3 classes: Happy, Sad, Angry. However, this is not a valid amount of classes

### Improvement Possibilities
1. Cleaning dataset 
  - Remove ambiguity
  - Remove mislabeled
2. Create balanced dataset

## How To Use The App
This app supports two usage scenarios: Live Camera and Static Image.

### Live Camera scenario
It uses the camera preview as input and contains two workflow: object detection & visual search, and barcode detection. There's also a Settings page to allow you to configure several options:

* Camera
Specify the preview size of rear camera manually (Default size is chose appropriately based on screen size)
* Object detection
Whether or not to enable multiple objects and coarse classification
* Product search
Whether or not to enable auto search: if enabled, search request will be fired automatically once object is detected and confirmed, otherwise a search button will appear to trigger search manually
Required time that the auto-detected object needs to be focused for being regarded as user-confirmed

### Static Image scenario
It'll prompt to select an image from the Image Picker, detect objects in the picked image, and then perform visual search on them. There're well designed UI components (overlay dots, card carousel etc.) to indicate the detected objects and search results.

Note that the visual search functionality here is mock since no real search backend has set up for this repository, but it should be easy to hook up with your own search service (e.g. Product Search) by only replacing the SearchEngine class implementation.
