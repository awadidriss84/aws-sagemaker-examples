# PPE Detector for Laboratory Safety
[The PPE Detector for Laboratory Safety](https://aws.amazon.com/marketplace/pp/prodview-6gvzwuebead3o) - is a real-time computer vision model for PPE non-compliance detection in the laboratory setting. It analyzes live footage from high-resolution cameras to identify people missing any of the PPE items specified in safety regulations. The solution detects four object classes: Coat, Glasses, Glove, Mask. The ML model can be used in schools and universities, industry, government, military facilities, and other laboratories.

[![AWS Marketplace](AWS-Marketplace.png)](https://aws.amazon.com/marketplace/pp/prodview-6gvzwuebead3o)

## Usage Information

Using our model for real time prediction is as simple as this:

```python
predictor = sagemaker.predictor.RealTimePredictor(
    ' your endpoint name ',
    sagemaker_session=sagemaker.Session(),
    content_type="image/jpeg"
)

with open('data/sample_image.jpg', 'rb') as img:
    img_bytes = bytearray(img.read())
    result = predictor.predict(img_bytes).decode("utf-8")
```

Also we've published two notebooks showing how to use our model:
* [Using-Laboratory-Personal-Protection-Equipment-Detector-Endpoint.ipynb](Using-Laboratory-Personal-Protection-Equipment-Detector-Endpoint.ipynb) notebook shows how you can use Python API to perform inference on endpoint created from the model
* [Using-Laboratory-Personal-Protection-Equipment-Detection-model.ipynb](Using-Laboratory-Personal-Protection-Equipment-Detector-Endpoint.ipynb) notebook shows how you can use Python API to run the full scenario:
    * deploy our model to create an endpoint
    * run Real Time inference on endpoint using local image
    * visualize  and save the prediction on original image
    * run Batch Transform job to perfom the inference on your data stored in Amazon S3 bucket

## Input\output data examples

* You can find sample input data in [demo_input](sample_data/demo_input) folder
* [demo_output_images](sample_data/demo_output_images) folder contains images with detections predicted by the model and visualized using `utils.visualize_detection` method
* [demo_raw_output](sample_data/demo_raw_output) folder contains raw output generated by our model using `Batch Transform` approach

## Sample detection results:

![PPE Detector for Laboratory Safety output example](sample_data/demo_output_images/image1.jpg?raw=true)

![PPE Detector for Laboratory Safety output example](sample_data/demo_output_images/image2.jpg?raw=true)

![PPE Detector for Laboratory Safety output example](sample_data/demo_output_images/image3.jpg?raw=true)

![PPE Detector for Laboratory Safety output example](sample_data/demo_output_images/image4.jpg?raw=true)

![PPE Detector for Laboratory Safety output example](sample_data/demo_output_images/image5.jpg?raw=true)

![PPE Detector for Laboratory Safety output example](sample_data/demo_output_images/image7.jpg?raw=true)