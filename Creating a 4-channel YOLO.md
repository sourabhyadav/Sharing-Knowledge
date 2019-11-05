# Creating a 4-channel YOLO training using Darknet
I was using trying to train a Yolo network on 4-channle as input training images. 4-channels images would be required for using object detection using depth image or optiflow based object detection could be useful. I thought to add optical flow as flow data along with rgb data to create object detection for moving objects.

**Use [Darknet](1) as the framework it does not contain support for 4-channels as the input.** And I did not find any Git repo for making it work. So I figured out how to make it happen.

Following are thing sdone to make 4-channel training Yolo work:
1. Create the 4-channel images and save it is as .png, **Why png** as jpg images does not contain 4-channels stuff. 
2. In the cfg file make channels = 4
3. Remove opencv flag from Makefile OPENCV=0
4. In the image.c file hsv_rgb and rgb_hsv function has an assert for 3 channels you should remove this assert 
That's it.

Now you can train the model. It worked for me.

[1]:https://github.com/AlexeyAB/darknet
