# keras-yolo3-Mobilenet

Cloned from [Adamdad](https://github.com/Adamdad/keras-YOLOv3-mobilenet).
See original repo for full doc.

I created yolo_image.py and modified yolo.py a bit so that
images can be batch-processed and the results are stored
as a jpg file with boxes plus a json file
with coordinates and other textual information.
See [YOLO 自動框出相片裡的人/動物/生活用品](https://newtoypia.blogspot.com/2018/10/yolo.html) for details.
That post refers to my clone of the original yolo,
but the .py modifications are pretty much copied directly to this repo.

## Quick Start

Preparation:
1. Clone this repo into $HOME/git/ as $HOME/git/keras-YOLOv3-mobilenet/
1. Create $HOME/pictures/ and put .jpg files in it.
1. Create an empty $HOME/models/ for storing downloaded and converted models.
1. Create an empty $HOME/result/ for storing results.
1. Start the keras docker: `docker run --name keras -it -v $HOME:/srv gw000/keras:2.1.4-py3-tf-cpu bash`

Then inside the docker:
```
pip3 install Pillow matplotlib opencv-python

cd /srv/git/keras-YOLOv3-mobilenet/
wget https://pjreddie.com/media/files/yolov3.weights -O ../models/yolov3.weights
python3 convert.py yolov3.cfg ../../models/yolov3.weights ../../models/yolo.h5
time python3 yolo_image.py --model_path ../../models/yolo.h5 --outdir ../../result/ ../../pictures/*.jpg
```
