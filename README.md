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

## Install v4l2loopback
sudo apt install v4l2loopback-dkms v4l2loopback-utils

## Stream desctop to video2
sudo modprobe v4l2loopback
ffmpeg -f x11grab -r 15 -s 1024x768 -i :0.0+0,0 -vcodec rawvideo -pix_fmt yuyv422 -threads 0 -f v4l2 /dev/video2
