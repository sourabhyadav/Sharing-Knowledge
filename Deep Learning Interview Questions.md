##Deep Learning Typical Interview Quetions

Following are few theoretical questions people ask. You might answer all 

**Importance of random weight initialisation?**
* To add non-linearity to the network, otherwise it becomes a simple high-dimensional linear model similar to like SVN.  

**Effect of Training a shallow-network vs Deep-network?**  

**Why convolution, why not direct MLP?**  
* Less params than MLP so that they becomes practically implementable
* Spatial understanding and understanding spatial features
* Makes the system translational invariant 


**Accuracy measures and their uses?**  
* Precision
* Recall
* Accuracy
* F1-Score
* RoC Curve
* PR Curve
* mAP  

**Why MaxPool? Why not any other function?**  

**What is ResNet? Advantages of ResNet? What problems were solved by ResNet?**    
* It solves Vanishing Gradient problem  

**What is Vanishing Gradient Problem in DNN?**  

**Why use Relu? Why we canot use sigmoid or tanh activation function?**  

**What is softmax? When to use softmax?**  

**What is bias-vaiance problem?**  

**Why 1x1 convolutions? How does it reduce computations?**
* Depth-wise directionality reduction  
* Makes input independent of size when compared to FC layer where input image has to be of fixed size due to FC layer is hard-coded stuff.  
* Show calculation of how much 1x1 conv helps in reducing the computation. Refer to 1x1 conv.md in the same repo.  