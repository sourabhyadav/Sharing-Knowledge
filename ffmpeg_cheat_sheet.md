# Few frequently used ffmpeg commands collection

**Dumping all the frames from a video using ffmpeg**
```
fmpeg -i input.mp4 img_%5d.jpg
```

**Select 1 frame out of every 10 frames**
```
ffmpeg -i input.mov -vf "select=not(mod(n\,10))" -vsync vfr -q:v 2 img_%03d.jpg
```

**Finding video length in hh:mm:ss format**
```
ffmpeg -i ch01_00000000034000000.mp4 2>&1 | grep "Duration"
```

**Rescaling the size of frame of a video**  
```  
ffmpeg -i input.mov -vf scale=720x406 output.mov 
```  
For more options visit [here][1]
[1]: https://video.stackexchange.com/questions/9947/how-do-i-change-frame-size-preserving-width-using-ffmpeg/9967

