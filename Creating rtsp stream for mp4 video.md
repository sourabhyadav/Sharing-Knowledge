Open VLC:

Media -> Stream …

In File tab click Add…; select a video file (its better if its > 1 minute)

Click on Stream, in Source click Next

Select RTSP in “New destination” and click Add

In RTSP tab Path should be /stream.asx

In Transcoding Options, Profile select “Video –H.264 + MP# (MP4)”; click Next

Click Stream button

 

Open another VLC instance:

Media - > Open Network Stream…

Give in network URL: rtsp://:8554/stream.asx or rtsp://<your local IP adress>:8554/stream.asx 

Click Play

 

On the second VLC instance you should be able to see the video with some delay / compression. This is similar to streaming from camera.

[Another source (I did not try this)][1]

[1]: https://support.spinetix.com/wiki/Tutorial:Streaming_using_VLC
