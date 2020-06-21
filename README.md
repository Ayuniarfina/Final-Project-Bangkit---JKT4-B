# ML Face Expressions Recognitions App

This app demosntrate how to build 

## Steps to run the App


## Model ML


## How To Use The App


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
