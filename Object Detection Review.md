## Object Detection Review 
Following is the summary of some of the famous Object Detection methods. This might contain hand-crafter methods as well as new Deep Learning Methods. 
I will also include famous datasets for the same whenever required.

**Object detecation publications per year**

Most of the early object detection algorithms are based on hand-crafter features.

[**Voila Jones(VJ) Face Detetor:**](1)

* It was 1st famous real-time object detection(face) detection paper at that time.
* It applied moving window for visiting all possible location  at multiple scale to detect all the face in the image.
* Few important concepts to learn from VJ detector is:
1. **Integral Image:** it is an method to speed-up box filtering. This also improved performance of the Harr-Cascade calculation by making the computation independent of window size. This has drastacally reduced the time for feature representation of the image.
2. **Automatic Feature Selection:** It uses adaboost to select features for face detection. Previous algorithmns uses manually selected Haar basis filters.
3. **Detection Cascades:** VJ detector used cascaded detection pipeline similar to like present day Deep Network layers. It was designed in such a way to reduce computations on background.

[**Histogram of  Oriented Gradients(HOG) Detector:**](2)

* This detector was well-known for imporvement in scale-invarient feature transform. It was also good at different shape objects.
* Primarally esigned for detecting Pedestrains but can be used for diffrent classes as well.
* For multi scale etection it rescales input image while keeping the size of feature window same
* It uses dense grid of uniformaly seperated cells.
* It computtes major direction of the gradients using Histogram for each cell to define it as a feature of a particular object.


[**Active Shape Model and Active Appeareance Model:**](3)

* This family of detectors are well know for detecting the shape of the any general object.
* **While training** an object is represended as set on n-points around its shape. We need to provide lots of images and annotate it with the same n-points . The goal of training was to learn the principal direction for each point to fit to a particular object boundary.
* It ueses the Principal Component Analysis to reduce the search space for each of n-points.
* **While testing** it starts with a user initialed seed point to start the best-fit search for each n-points around the object. It terminates either no points are updated or max-iteration haults.


[**Deformable Part-basd Model:**](4)

* It uses simple technique of "divide and conqure"
* You can conside **training process** is like dividing the object into smaller parts for its learning
* **Testing** is like ensemble of all these parts to form or detect a particular object.


## Deep Object Detection:
The performance of hand-carfted methods have reached to platue. adly you would see any major improvements in Object Detection area during 2009-2012. With the advent of deep learning methods object detection has reached to new lavel of accuracies.
Prior to deep networks the algorithms were hard used in real-world application due to multiple factors like computatiion speed and robustness to real-world setting. Moreover, these methods are non-generic in nature. 
Deep methods solved lot of these problems and now it can be used in commercial deices.

There are two major methodlogies famous in Deep object detection space. Both has its own pro and cons depends on your need and computational capacity.

###Two-stage Networks:**
These kind of methods uses 3 passes for object detection. In the first phase it detects potential areas of objects to be present. Later it localizes and detects the object in the iamge.

[**Region Convolutional Network (R-CNN):**](5)

* **Selective Search:** R-CNN netowrk uses selective search method to find out object proposal i.e. probable object bodes. These proposal is rescalled to a fixed size image.
* Later this proposal image is fed to **CNN model like AlexNet or VGG** which is pre-trained on ImageNet.
* At the end a **SVM classifier** is used to detect the presence of object in each proposal and categories them.
* Although it has impvod the performance to a significant extent but it faces major drawbacks are selective search is computationally expensive, redundant feature computation due to overlapping proposals.

[**Spatial Pyramid Pooling Network (SPP Net):**](6)

* For using a previous CNNs like AlexNet o VGG requires fixed size input like 224x224. So when the proposals ae rescalled to a paricular size the CNN face to generalize the for the same object. 
* SPPNet adds a spatial pyramid pooling layer which helps network to  generate proposals of fixed sizes without resizing the iamge. This makes it independent of the size of the iamge or object. 
* It also helps in generalizing for different size of a particular object.
* With SPP we can compute the proposals or feature maps only once per iamge thus need not to compute conv featues repeadtely which improved the speed of object detection.

[**Fast R-CNN:**](7)

* Basically it is combination of R-CNN and SPP Net into a single process but with major drawback is its speed bottleneck is detecting fixed size proposals like SPP Net.
* It is 200 times faster than R-CNN. It increased mAP to 70% compared to R-CNN which was at 58% on PascalVOC 2007 dataset.

[**Faster R-CNN:**](8)

* It was first end-to-ed conv net or object detection with a near realtime performance. The major achievement are: (COCO mAP@.5=42.7%, COCO mAP@[.5,.95]=21.9%, VOC07 mAP=73.2%, VOC12 mAP=70.4%, 17fps with ZF-Net
* **Region Proposal Network:** The main contribution of Faster R-CNN is that it uses a CNN to produce candidate regions. 
* **Feature extraction Layer pr ROI pooling layer** is used to extract important features from the generated proposals 
* **Detection Layer** is used to regress the size of the bounding box of the selected regions.
* All these modules were build into a single network for an end=to-end training whic makes it a unified network for object detection.
* RPN reduces the bottleneck of the computation time required to produce proposals.

[**Feature Pyramid Networks (FPN):**](9)

* Most of te R-CNN family netowrk or othr object detection network uses detection regression only at the top-layers. Such technique produces poor results on objects with smaller size or vary at a large scale.
* The idea behind FPNs is simple it uses features at multiple scale to detect the object at different varying scale.
* It was studied that deeper layer helps in categorizing the classes but does not help much on localizing the objects. 
* A faster R-CNN with FPN produced state-of-the art results on MS COCO dataset :MSCOCO dataset without bells and whistles (COCO mAP@.5=59.1%, COCO mAP@[.5, .95]=36.2%). 


**Single-stage Networks:**

This kind of networks use link CNN trunk to detect and categorise the class of the object in a given image.

[**You Only Look Once (YOLO v1):](10)

* Basically it uses single CNN trunk for detection and classification
* It logically divides the image into a fixed size grids and tries to detect multiple dimention objects into each grid box.
* Later it uses NMS to reduce false boxes using IoU.
* It uses 3 different loss functions: objectness loss, classification loss and detection regression loss.
* This is much faster than Faster R-CNN with similar accuracies. It runs at 45fps with VOC07 mAP=63.4% and VOC12 mAP=57.9%


[**Single Shot Detector (SSD):**](12)

* SSD is similar to YOLO but it uses detection for from multiple stages of the network
* Basically YOLO faces accuracy loss in accurate bounding box detection and also not suitabl for small objects
* SSD solved the above 2 issues with YOLO by pooling features from initial layers in the network.
* SSD has advantages in terms of both detection speed and accuracy (VOC07 mAP=76.8%, VOC12 mAP=74.9%, COCO mAP@.5=46.5%, mAP@[.5,.95]=26.8%, a fast version runs at 59fps)


[**YOLO v2 & v3:**](11)

* Same author made further improvements in base YOLO to improve it furthr on accuries and performance
* **Anchor Boxes** generated from the ground-truth are used as prior for improving the detection accuracies.
* Added skip layers to use features from initila layers befoe they get vanished and not used. This help to improve detection at small objects.

[**RetinaNet:**](13)

* Normally it is observed that one-stag netwok accuracies is always trailing on than 2-stage networks.
* **Focal Loss: **RetinaNet improves the accuracies by introducing the new loss function called focal loss. 
* It was observed that due to foreground-backgound class imbalance one-stage netork accuracies suffers, thus the new loss function, which is modification to standard cross-entropy loss, tries to penalize the backgound and put more focus on misclassified examples during training.
* Focal Loss enables the one-stage detectors to achieve comparable accuracy of two-stage detectors while maintaining very high detection speed. (COCO mAP@.5=59.1%, mAP@[.5, .95]=39.1%).

To be continued...







[1]: https://dl.acm.org/citation.cfm?id=966458
[2]: https://ieeexplore.ieee.org/document/1467360
[3]: https://www.mathworks.com/matlabcentral/fileexchange/26706-active-shape-model-asm-and-active-appearance-model-aam
[4]: http://www.embeddedvisionsystems.it/solutions/ip2lib/117-dpm
