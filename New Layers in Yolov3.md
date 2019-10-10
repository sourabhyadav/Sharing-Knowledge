# New Layers in Yolov3 cfg file

Here I am going to write about Yolov3 layers and its teminologies used in Yolov3.cfg file.
Basically author have used different names which creates confusion sometimes.
Other than conventional terms like Convolutional, Relu, batch_normalize, stride, pad, filters, kernel size and activation.

You will see 4 new layers named shortcut, updample, route and yolo. Let me explain each of these:

**shortcut**: This is nothing but a skip connection inspired by ResNet like structure. Shortcut layer will contain params like **from** which has a -vie number which shows how many layers to skip.

**route**: This is nothing but a feature concat layer. It has a params like **layers** which has 2 numbers which shows from which layers concat has to happen.

**yolo**: It is nothing but actual detecion layer where the bounding box calculation is doing based on **anchor boxes** during training. While testing this layer predicts boudning box and class score and objectness score. 

**upsample**: It is used to upsample features before detection layer as the deteciton layer prediction size goes like this **N x N x [B + (4 + 1 + C)]** where N is the grid size which is calculated dynamically based on input layer. As the nextwork goes deeper the feature map size reduces thus we need to updample the feature maps to always fit into the formula. So in Yolov3 you will find 2 updample layers as there are 3 scales detections.
