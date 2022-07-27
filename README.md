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

## Usage instructions
<!--
Give details on how to install fork and install your project. You can get all of the python dependencies for your project by typing `pip3 freeze requirements.txt` on the system that runs your project. Add the generated `requirements.txt` to this repo.
-->
- Run the yolov4-Deepsort.ipynb notebook in Google Colab.
- You must input a mp4 video or you will need a webcam to track people for this model.
