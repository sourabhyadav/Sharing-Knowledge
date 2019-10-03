# YCrCb 
It is yet another colorspace in image processing frameworks. It is similar to RGB color space but it is more designed based on how human eyes percieve colors.

**Y**: 
Represents **Luma** componet. Also represents brightness of the color
- Our eyes are more sensitive towards this component. 
- In image processing it also provides **Gray Image**

Cr and Cb represents **Chrome** components of the color 

**Cb**:
Cb is the blue component relative to the green component

**Cb**:
Cr is the red component relative to the green component

When in JPEG compression, it uses these sensitivities of the human eye and eliminate the unnecessary details of the image.

It is also called YUV space. It takes less memory thatn  RGB space. E.g. Amount of memory required to store a M x N RGB image is M x N x 3 bytes for the same image you can store in YUV space M x N x 1.5 bytes **ONLY!**
YUV channel is arranced as M x N Y then m x N/4 U and M x N/4 V. Thus it takes less memory.
