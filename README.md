# Object Detection and Tracking

< br />

# Masked R-CNN
##### Masked Region based Convolution Neural Networks
Run via AWS SageMaker using a notebook instance of ml.p2.xlarge (GPU CUDA-capable) and an elastic inference of ml.eia1.medium to save on costs. In order to run an elastic inference select the Oregon server.
< br />
### Primer on Masked R-CNN:
< br />
#### Well what is it?
Instance segmentation. Combining object detection and semantic segmentation producing instance segmentation. Object detection is acheived by finding and classifying the variable number of objects within an image, image to image generating a bounding box or a region of interest (ROI). Semantic segmentation is acheived through understanding the image at the pixel level via assigning an object class to each pixel in the image creating a mask from each ROI. Object detection in Masked R-CNN uses an architecture similar to Faster R-CNN to generate the ROIs, whereas semantic segmentation uses a fully convolution network (FCN) to predict the mask from each ROI. Combining Faster R-CNN and FCN results in Masked R-CNN, Masked R-CNN also uses ROIAlign which dosen't quantize the stride resulting in the preservation of the spatial orientation of features with no loss of data as well. FCNs are important for this as well as convolution layers retain the spatial orientation which is fundamental to location specific tasks like creating an object mask.

< br />

#### What's special about Masked R-CNN?
Instance segmentation at the pixel level as compared to R-CNN, Fast R-CNN, and Faster R-CNN.



< br />

