# ar-pi-playground



## List formats
ffmpeg -f v4l2 -list_formats all -i /dev/video1

## List devices
v4l2-ctl --list-devices

## Add video device
sudo modprobe v4l2loopback

## List Codecs and formats
ffmpeg -codecs
ffmpeg -formats

## Image as video device
ffmpeg -loop 1 -re -i Early_flight.jpg -f v4l2 -vcodec rawvideo -pix_fmt yuyv422 /dev/video2

## Connect video device as output USB camera
~/uvc-gadget/uvc-gadget -v /dev/video2 -u /dev/video1 -r 1 -f 0
