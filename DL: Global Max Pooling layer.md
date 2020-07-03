The Global Max Pooling Layer (GAP) Layer.  
In a way it is an agressive way to do dimentionality reduction. It converts wxhwd tensor to 1x1x#filters.  
It was introduced in the paper [Network-in-Network][1] paper. It was used to eliminate the FC layer number of parameters, which inturn avoid overfitting and redices the number of paramters. Also it was used to learn complex funtion due to averaging.
A good explaination is found here: [Coursera][2], [blog][3], [diff types of pooling][4], [decent intro][5]

[1]: https://arxiv.org/pdf/1312.4400.pdf  
[2]: https://www.coursera.org/lecture/convolutional-neural-networks/networks-in-networks-and-1x1-convolutions-ZTb8x 
[3]: https://adventuresinmachinelearning.com/global-average-pooling-convolutional-neural-networks/  
[4]: https://www.machinecurve.com/index.php/2020/01/30/what-are-max-pooling-average-pooling-global-max-pooling-and-global-average-pooling/  
[5]: https://alexisbcook.github.io/2017/global-average-pooling-layers-for-object-localization/
