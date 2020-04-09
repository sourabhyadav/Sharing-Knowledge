**Install tensorflow using ufom/deepo**  
```docker run -it --gpus all --shm-size=12G -v /datadrive/:/whatever/ --name=Satan ufoym/deepo: tensorflow-py36-cu100``  `
* This will have tensorflow installed  

**Install pycocotools**  
```git clone https://github.com/cocodataset/cocoapi.git```  
* ```cd PythonAPI/```  
* Edit Makefile. Replace python to python3.  
* Run: ```make all; make install ```  


