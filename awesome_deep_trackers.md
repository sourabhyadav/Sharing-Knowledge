## A practical guide to choose different state-of-the-art trackers

Here I tried to address the issue of choosing the right tracker for any given application or project. Many times MOT quantitative measures (MOTA, MOTP, etc.) are not just enough to choose a tracker. Choosing trackers is relatively difficult because of assumptions made for writing tracker algorithms, a wide variety of practical usage concerns, and things associated with the temporal domain. A few notable attributes are:  
 
Few notable attributes are:
 * track object ID generation
 * track object re-identification
 * missing-track identification 
 * partial/full occlusion handling 
 * multi-class tracking
 * view point variation
 * stationary vs moving camera etc.


Below are a few latest trackers with deep learning capabilities and corresponding insights to each of them:  

**Testing Setup:**  

* These trackers are tested on 6 testing videos taken from static CCVT camera where humans are walking.    
* All the timing performance is taken on NVIDIA RTX 2080 10GB.  
* Trackers are tested with default settings provided by the author's git repo.  
* We used Yolo v3 (coco 80 classes) as Object detection for all the trackers.  

**1. [Simple online and realtime tracking][1]**    
Publication year: ICIP 2016  
Official Github: [link][2]

  
**Pros:**  
This tracker comes up with its own track ID generation.    
It uses Kalman filter for track location prediction which is very fast.    
It has its own matching mechanism cost function to assign IDs.  
Does good with different view-points.  

**Cons:**  
Tracking accuracy is highly sensitive to object detection accuracy.    
To get best performance you have to provide an object bounding box for each frame.    
Variety of tunable thresholds to play around.    
Object missing mechanism is poor.  
Consecutive 3 detections are required to generate track ID.  



[1]: https://arxiv.org/abs/1602.00763
[2]: https://github.com/abewley/sort

**2. [Simple Online Realtime Tracking with a Deep Association Metric][3]**  
Publication Year: ICIP 2017  
Official Github: [link][4]  

**Pros**  
This tracker comes up with its own track ID generation.    
It uses Kalman filter for track location prediction which is very fast.   
Re-identification is done using a trained model for humans. We can retrain for our use case.  
It has its own matching mechanism cost function to assign IDs which uses IoU and deep feature association.  
Training script is available.  

**Cons:**  
Tracking accuracy is highly sensitive to object detection accuracy.  
To get best performance you have to provide object bounding box for each frame.  
Variety of tunable thresholds to play around.  
Object missing mechanism is poor.  
Multi-class traking is bit of a problem as we need to rain new model for new objects to be tracked.  
Sensitive towards different view-points  basically it depends on training the feature extractor as well.  
Consecutive 3 detections are required to generate track ID.  


**Performance:**  23-25 fps  


[3]: https://arxiv.org/abs/1703.07402v1
[4]: https://github.com/nwojke/deep_sort/tree/280b8bdb255f223813ff4a8679f3e1321b08cdfc


**3. [Fast online object tracking and segmentation: A unifying approach][5]**  
Publication Year: CVPR 2019  
Official Github: [link][6]  

**Pros**  
This does not have frame ID generation than needs to be done externally. 
Provides tighter bounding box.  
Provides segmentation mask of the given object.    
Re-identification is done using a trained model for humans. We can retrain for our use case.  
It has its own matching mechanism cost function to assign IDs which uses IoU and deep feature association.  
Training script is available.  
Multi-class tracking is possible with any multi-class pre-trained model. 

**Cons:**  
Only single time detection would work for tracking.   
Does a good job even if detection accuracy is very poor.     
The object missing mechanism is poor.  

**Performance:**  45-50 fps 
 

[5]: https://arxiv.org/abs/1812.05050  
[6]: https://github.com/foolwood/SiamMask

**4. [Towards Real-Time Multi-Object Tracking][7]**  
Publication Year: CVPR 2019  
Official Github: [link][8]

**Pros**  
This tracker comes up with its own track ID generation.      
Re-identification is done using a trained model for humans. We can retrain for our use case.  
Does object detection and appearance tracking jointly.  
It has its own matching mechanism cost function to assign IDs.  
Training script is available.  
Multi-class tracking is possible.  
Less sensitive towards different view-point of objects.  

**Cons:**  
Tracking accuracy is highly sensitive to object detection accuracy.  
To get the best performance you have to provide object bounding box for each frame.  
ID switch is very frequent.  
Performance depends on how well the object detector is trained.  

**Performance:**  21-25 fps


[7]: https://arxiv.org/abs/1909.12605
[8]: https://github.com/Zhongdao/Towards-Realtime-MOT

**5. [LightTrack: A Generic Framework for Online Top-Down Human Pose Tracking][9]**  
Publication Year: CVPR 2019  
Official Github: [link][10]  

**Pros**  
This tracker comes up with its own track ID generation.      
Re-identification is done using a trained model for human poses.  
Does object detection and appearance tracking jointly.  
It has its own matching mechanism cost function to assign IDs.  
Training script is available.  
Less sensitive towards different view-point of objects.  
We choose different detection and pose CNNs to try out with this framework.  
ID switch is very good.  
Track-loose is easily identified.

**Cons:**  
Performance depends on how well the object detector and pose detector are trained.  
Multi-class tracking is NOT possible as it depends on Human Pose.  

**Performance:**  5-6 fps

[9]: https://arxiv.org/abs/1905.02822
[10]: https://github.com/chenhaomingbob/test_track

