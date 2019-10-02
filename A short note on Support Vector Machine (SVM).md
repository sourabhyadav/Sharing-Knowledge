# Support Vector Machine
**Why SVM?**: When we have 2 categories in your dataset but no obvious linear classifier that separates them in a nice way we use support vector machines (SVM)
Basically, the support machine transforms the given data from lower dimensional space to higher dimensional space to find the maximum marginal classifier (decision boundary) to classify them.

**Explanation**
It starts with Bias Variance Trade-off in any classification problem or ML problem. 

Taking an example of a 1-dimensional dataset e.g.Obess vs not Obsess wrt to the only weight of the person. Here we can choose the best threshold to classify those. **But how do we choose the best threshold which separates the dataset properly?**

To solve this dilemma we find maximum margins from both the classes and put the threshold which is called **Maximum Margin Classifier**. 
Basically a **margin** is the distance between to nearest observations.

The major **drawback of Maximum Margin Classifier** is they are very sensitive to any outlier which is close to the boundary of the other class. To mitigate this problem we must allow misclassification while choosing the decision boundary. This is what we called **bias-variance trade-ff**.  

So when we allow the misclassifications, the distance between the observations and the threshold is called **Soft Margin**. **How do we know which is best soft margin?** 

The answer is **Cross Validation**. That is nothing but try on your validation dataset using this given threshold.

We use these soft margins to determine the thresholds we are using a **soft margin classifier aka Support Vector Classifier**.

**Support Vector** are the observations in the training data which lie within the soft margin are called support vectors.

**Properties of support Vector:**
When we have our observations in 1 dimensional then support vector classifier is a Point
When the dataset is 2-dimensional then the support vector classifier is a 1-D line.
When the dataset is 3-dimensional then support vector classifier is plane or 2-D plane.
When we have higher dimensional we have support vectors as hyperplanes.

Support vectors are pretty cool as:
1)  They can handle basic outliers
2) They can handle overlapping observations

**BUT** if the dataset contains a lot of overlap or difficult to separate the dataset in a given dimension, then no matter where we put our classifier we might get a lot of misclassification, **THEN** we use **Support Vector Machine**.

The basic institution is we transform the dataset into some higher-order function called **Kernel functions** then apply the classifier into that dimension to form a **classifier boundary or Decision bounday**.
For eg: let say we have a lot of overlapping dataset into 1-D space where maximum margin classifier and support vector classifier fails. We may transform this dataset to at least 2-D space using a simple squared function (a simple Kernel function) for all the observation then we use apply maximum margin classifier to find the decision boundary.

**The main ideas of SVM**:
1) Start with data in relatively low dimensional 
2) Move the data into a higher dimension
3) Find the support vector classifier which classifies the data set into 2 groups

**That's it!!!**

How do we choose any particular Kernel Function? 
I think it depends on the application and dataset complexity. 
To make the transform mathematically possible the classifier uses to transform it wrt to each observation points against others and then it is used to find the decision boundary.

**Note:** another commonly used kernel is **Radial Bais Kernel** . Radial Basis Kernel finds the support vecotr classifier in infinite dimensions. I don't have more details about this kernel function as of now.

**The Kernel Trick** basically kernel function does not transform the complete dataset into a higher dimension because sometime it might overshoot the amount of computation and memory required to do so. Thus, the kernel trick reduces the computations by avoiding the math that transforms the data from low to high dimensions and it makes calculating relationships in the infinite dimensions used by  Radial Bias Kernel to compute the bset classifier in infinite space.  
