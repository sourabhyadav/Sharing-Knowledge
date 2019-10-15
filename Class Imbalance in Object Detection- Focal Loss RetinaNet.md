# A Short Note on Class-Imbalance Problem in Object Detection

**What is the class imbalance problem?**
In supervised learning-based Object Detection require training dataset for each of the object classes. Sometimes it may happen that you might not have enough or equal dataset for a particular class.
This leads to a problem called class imbalance problem while training the Object Detection Network. E.g. if you wanted to train a universal vehicle detector, you might find more images for cars and bikes but you might have very fewer images for carrier vehicles like mini-trucks, etc,

**How does class imbalance problem effect?**

Performace on these low classes would be very low. It is because the network has not seen many images for such classes and will overlook features from such classes.

**Solution for class imbalance problem?**

[Easiest solution][1] is you sample the augmentation to avoid class imbalance i.e. Oversample rare classes dataset and undersample frequent datasets. This might help in some cases.

Another solution is:
**[The Focal Loss:][1]**

Focal loss (FL) adopts another approach to reduce the loss for a well-trained class. So whenever the model is good at detecting background, it will reduce its loss and reemphasize the training on the object class.
This is achieved by extending the cross-entropy loss while penalizing the loss for lower weights.

[1]: https://medium.com/@jonathan_hui/what-do-we-learn-from-single-shot-object-detectors-ssd-yolo-fpn-focal-loss-3888677c5f4d
[2]: https://medium.com/styria-data-science-tech-blog/using-yolo-algorithms-to-conquer-the-global-data-science-challenge-bee7793b0e54
