# The 1x1 Convolution:
- Used as dimensionality reduction on [depth of the network][1]
- In googleNet it was used to reduce the number of computations. Which helps to increase the network width and depth.
- It was first introduced in paper [Network-in_network][2].
- This helps to remove FC layers and make the network genric for the input size

A basic calculation for dimensionality reduction goes like this:[1]  
**say we have a input tensor of 14x14x480, we want output of 14x14x48 filter size is 5x5:**  

**Without 1x1 conv:**  
filter size = 5x5x480
Each filter will be applied to 14x14 locations. Assuming the we keep pad=2 and stride=1
Thus to produce 1 feature map we need to have 5x5x480x14x14 operations. and this will be done for total #48 filers. Thus, the total number of operations required are:5x5x480x14x14x48 = **112.9M**

**With 1x1 Conv:**  
Here, what we do is 1st we apply 1x1x(480)x16 conv and then 5x5x(16)x48 conv    
Initial filter size: 1x1x480  
Each filter will be applied to 14x14 locations.  
Thus to produce 1 feature map we need to have 1x1x480x14x14 operations. and this will be done for total #16 filers. Thus, the total number of operations required are:1x1x480x14x14x16 = **1.5M**. Now the output shape of the tensor is 14x14x16  
Then we apply 5x5x48 conv to above tensor to get our desied output shape i.e. 14x14x48   
Thus to produce 1 feature map we need to have 5x5x16x14x14 operations. and this will be done for total #48 filers. Thus, the total number of operations required are:5x5x16x14x14x48 = 3.7M.  
Total calculation are : 1.5+3.7 = **5.2M** calculation which is very less than **112.3M**  

Note: Kindly ignore spelling mistakes

[1]: https://medium.com/coinmonks/paper-review-of-googlenet-inception-v1-winner-of-ilsvlc-2014-image-classification-c2b3565a64e7
[2]: https://arxiv.org/abs/1312.4400?context=cs

