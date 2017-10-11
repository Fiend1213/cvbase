## Video

This module provides friendly apis to read and convert videos.

```python
import cvbase as cvb

video = cvb.VideoReader('test.mp4')
# access basic info
print(len(video))
print(video.width, video.height, video.resolution, video.fps)
# iterate over all frames
for frame in video:
    print(frame.shape)
# read the next frame
img = video.read()
# read a frame by index
img = video[100]
# split a video into frames and save to a folder
video.cvt2frames('out_dir')
# generate video from frames
cvb.frames2video('out_dir', 'test.avi')
```

There are also some methods for editing videos, which wraps the commands of ffmpeg.

```python
import cvbase as cvb

# cut a video clip
cvb.cut_video('test.mp4', 'clip1.mp4', start=3, end=10, vcodec='h264')
# join a list of video clips
cvb.concat_video(['clip1.mp4', 'clip2.mp4'], 'joined.mp4', log_level='quiet')
# resize a video with the specified size
cvb.resize_video('test.mp4', 'resized1.mp4', (360, 240))
# resize a video with a scaling ratio of 2
cvb.resize_video('test.mp4', 'resized2.mp4', ratio=2)
```