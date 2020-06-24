#Object Detection Evaluation Metrics  
List of few resolurces to evaluate Object Detection Model  

* [Evaluating Object Detection Models][1]: This provides a good overview of the various things to consider when working with object detection models.  
This also talks about the role of threshold for choosing the object detection model.  

* [Github implementation of mAP][2]: This is highly recommended repo. It contains Python implementation of mAP. It is very easy to use and works with YOLO format as well.  

* [Localized Recall Precision][3]: Basically this is a good acticle to understand the limitation of mAP. Here they introduces a new metric called Localized Recall Precision(LRP), which serves 2 purposes. 1. It consideres localization as a praramter for calulative mAP and 2. it helps in identifying the optimal threshold for a given class.  

* [Github implementation of LRP][4]: A implementation of LRP measure for COCO and VOC style detections.

[1]: https://manalelaidouni.github.io/manalelaidouni.github.io/Evaluating-Object-Detection-Models-Guide-to-Performance-Metrics.html  
[2]: https://github.com/rafaelpadilla/Object-Detection-Metrics
[3]: https://medium.com/swlh/on-object-detection-metrics-ae1e2090bd65
[4]: https://github.com/cancam/LRP/issues?q=is%3Aissue+is%3Aclosed
