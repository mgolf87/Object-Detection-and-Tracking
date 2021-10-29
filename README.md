# Object Detection and Tracking

<br />

# Masked R-CNN
##### Masked Region based Convolution Neural Networks
Run via AWS SageMaker using a notebook instance of ml.p2.xlarge (GPU CUDA-capable) and an elastic inference of ml.eia1.medium to save on costs. In order to run an elastic inference select the Oregon server.
<br />
<br />

### Primer on Masked R-CNN:

#### Well what is it?
Instance segmentation. Combining object detection and semantic segmentation producing instance segmentation. Object detection is acheived by finding and classifying the variable number of objects within an image, image to image, generating a bounding box or a region of interest (ROI). Semantic segmentation is acheived through understanding the image at the pixel level via assigning an object class to each pixel in the image creating a mask from each ROI. Object detection in Masked R-CNN uses an architecture similar to Faster R-CNN to generate the ROIs, whereas semantic segmentation uses a fully convolution network (FCN) to predict the mask from each ROI - computation of the mask is done in parallel with bounding box creation and classification. Combining Faster R-CNN with FCN on each ROI results in Masked R-CNN, Masked R-CNN also uses ROIAlign which dosen't quantize the stride (like ROIPool does) resulting in the preservation of the spatial orientation of features with no loss of data as well. FCNs are important for this as well as convolution layers retain the spatial orientation which is fundamental to location specific tasks like creating an object mask.
<br />

#### What's special about Masked R-CNN?
Single pixel level discrimination: 1 = pixel mask; 0 = elsewhere. Put another way, instance segmentation at the pixel level and no information loss via ROIAlign as compared to R-CNN, Fast R-CNN, and Faster R-CNN. R-CNN functions to: 1) generate a set of proposals; 2) run the images through a pre-trained alexnet; 3) run the box through a linear regression. As such, R-CNN is very slow as it requires thousands of forward passes for every image and separate training of three different models. Fast R-CNN speeds this up via ROI Pooling resulting in one pass per image, and by combining all models into one framework (feature extractor + classifier + regressor). However, Fast R-CNN is still slow, therefore, Faster R-CNN creates an attention mechanism using a region proposal network (RPN) which deals with the slowness of selective search. Thus, Faster R-CNN performs object detection in two stages: 1) it determines the bounding boxes via a RPN; 2) for each ROI it determines the class label via ROI Pooling.
<br />

