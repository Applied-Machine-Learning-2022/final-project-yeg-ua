[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-c66648af7eb3fe8bc4f294546bfd86ef473780cde1dea487d3c4ff354943c9ae.svg)](https://classroom.github.com/online_ide?assignment_repo_id=8127848&assignment_repo_type=AssignmentRepo)
<!--
Name of your teams' final project
-->
# AMLI Student Detection, Tracking & Counting
## [National Action Council for Minorities in Engineering(NACME)](https://www.nacme.org) Google Applied Machine Learning Intensive (AMLI) at the `University of Arkansas`

<!--
List all of the members who developed the project and
link to each members respective GitHub profile
-->
Developed by: 
- [Ellion Dison](https://github.com/ecdison) - `University of Arkansas`
- [Yasser Hassan](https://github.com/Yasserjr11) - `Virginia Tech` 
- [Gabriel Young](https://github.com/gabrielyoung02) - `University of Arkansas` 

## Description
<!--
Give a short description on what your project accomplishes and what tools is uses. In addition, you can drop screenshots directly into your README file to add them to your README. Take these from your presentations.
-->
The goal of this project is to detect and count the number of students in a classroom. To accomplish this, we used object tracking implemented with YOLOv4, DeepSort, and TensorFlow. YOLOv4 is a state-of-the-art algorithm that uses deep convolutional neural networks to perform object detections. The YOLO algorithm works by dividing the image into N grids, each having an equal dimensional region of SxS. Each of these N grids is responsible for the detection and localization of the object it contains. We can take the output of YOLOv4 feed these object detections into Deep SORT (Simple Online and Realtime Tracking with a Deep Association Metric) in order to create a highly accurate object tracker.
## Demo of tracker on humans
<p align="center"><img src="palace-test.gif"\></p>

## Demo Colab
<a href="https://colab.research.google.com/github/Applied-Machine-Learning-2022/final-project-yeg-ua/blob/main/Yolov5_DeepSort_Pytorch.ipynb#scrollTo=4yEraJfKhBku"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"></a>

## Tutorials

* [Yolov5 training (link to external repository)](https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data)&nbsp;
* [Deep appearance descriptor training (link to external repository)](https://kaiyangzhou.github.io/deep-person-reid/user_guide.html)&nbsp;

## Usage instructions
<!--
Give details on how to install fork and install your project. You can get all of the python dependencies for your project by typing `pip3 freeze requirements.txt` on the system that runs your project. Add the generated `requirements.txt` to this repo.
-->
1. Clone the repository recursively:

`git clone --recurse-submodules https://github.com/mikel-brostrom/Yolov5_StrongSORT_OSNet.git`

If you already cloned and forgot to use `--recurse-submodules` you can run `git submodule update --init`

2. Make sure that you fulfill all the requirements: Python 3.8 or later with all [requirements.txt](https://github.com/Applied-Machine-Learning-2022/final-project-yeg-ua/blob/main/requirements.txt) dependencies installed, including torch>=1.7. To install, run:

`pip install -r requirements.txt`

3. Make sure you replace the old track.py file with this [track.py](https://github.com/Applied-Machine-Learning-2022/final-project-yeg-ua/blob/main/track.py) after cloning the repository above.

## Tracking sources

Tracking can be run on most video formats

```bash
$ python track.py --source 0  # webcam
                           img.jpg  # image
                           vid.mp4  # video
                           path/  # directory
                           path/*.jpg  # glob
                           'https://youtu.be/Zgi9g1ksQHc'  # YouTube
                           'rtsp://example.com/media.mp4'  # RTSP, RTMP, HTTP stream
```


## Select object detection and ReID model

### Yolov5

There is a clear trade-off between model inference speed and accuracy. In order to make it possible to fulfill your inference speed/accuracy needs
you can select a Yolov5 family model for automatic download

```bash


$ python track.py --source 0 --yolo-weights yolov5n.pt --img 640
                                            yolov5s.pt
                                            yolov5m.pt
                                            yolov5l.pt 
                                            yolov5x.pt --img 1280
                                            ...
```

### StrongSORT

The above applies to StrongSORT models as well. Choose a ReID model based on your needs from this ReID [model zoo](https://kaiyangzhou.github.io/deep-person-reid/MODEL_ZOO)

```bash


$ python track.py --source 0 --strong-sort-weights osnet_x0_25_market1501.pt
                                                   osnet_x0_5_market1501.pt
                                                   osnet_x0_75_msmt17.pt
                                                   osnet_x1_0_msmt17.pt
                                                   ...
```

## Filter tracked classes

By default the tracker tracks all MS COCO classes.

If you only want to track persons I recommend you to get [these weights](https://drive.google.com/file/d/1gglIwqxaH2iTvy6lZlXuAcMpd_U0GCUb/view?usp=sharing) for increased performance

```bash
python track.py --source 0 --yolo-weights yolov5/weights/crowdhuman_yolov5m.pt --classes 0  # tracks persons, only!
```
## MOT compliant results

Can be saved to your experiment folder `runs/track/<yolo_model>_<deep_sort_model>/` by 

```bash
python track.py --source ... --save-txt
```


