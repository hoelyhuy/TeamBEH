---
layout: default
title: Final Report
---
## Video
## Project Summary
In our Minecraft-AI project, the agent tries to recognize different animals that appear in his view such as Pig, Rabbit, Ozelot, Sheep, Cow and then attempts to attack the Pig with a bow and arraows. Since we are interested in computer vision, we will attempt to use a real-time object detection algorithm called YOLO (You Only Look Once) to detect to detect which animals are in the agents view and where are the animals in the agent's view. (remaining: motivate the challenges of the problem, i.e why is it not trivial, and why u need AI/ML algorithms to solve it) 
## Approaches
Firstly, we write a program to generate the dataset, which is a set of many image captures of the agent's view. To do this, we start with designing the world, which is a piece of farmland surrounded by fences on four sides. On that piece of land, we spawn some animals (such as pigs, cows, sheeps, etc) at random locations. As the program starts, the agents takes a screenshot of his current view every 3 seconds. Malmo can give us the latest frame in the form of array of pixels. Given the array of pixels, we use image processing tools such as Pillow and opencv to convert the array of pixels into a .png file and store it to our computer. Before, we trained our neural network on a dataset of about 400 screenshots and the agent performs quite well. For final submission, we decided to train our neural network on about 1300 images to increase the accuracy of object detection.
<br />
<br />
After collecting the screenshots, we use an image labeling tool, which is called labelImg to create annotation files for the screenshots. An annotation file is an additional file that tells more information about the image; for this project, the additional information is which objects are in the image and where are they in the image. labelImg allows us to draw bounding box around an object and label that object, then generate an annotation file that is need for training. 
<br />
<br />
We will be using a real-time object detection algorithm called YOLO (You Only Look Once) to detect the animals in the agent's view. How the object detection algorithm works is that we apply a single neural network to the full image. This network divdes the image into regions and predict bounding boxes and probabilities for each region. These bounding boxes are weighted by the predicted probabilities. The model has several advantages over classifier-based systems. It looks at the whole image at test time so its predictions are informed by global context in the image. It also makes predictions with a single network evaluation unlike systems like R-CNN which require thousands for a single image. This makes it extremely fast, more that 1000 times faster than R-CNN and 100 times faster than Fast R-CNN. [YOLO: Real-Time Object Detection](https://pjreddie.com/darknet/yolo/)
<br />
<br />
Darknet is an open source neural network framework written in C and CUDA. It supports both CPU and GPU computation. To carry out training and input processing, we use darkflow, which is a translation of darknet to tensorflow. Once we are done with generating the screenshots and the annotation file, we store the screenshots and the annotation files in darkflow workspace. In addition to our own dataset, we also need YOLOv2 configuration file (with some small adjustments) and YOLOv2 weights to train. To train, we use Google Colab, which supports Python notebook and many other useful machine learning tools, plus a free GPU that is helpful for training.
<br />
<br />
Once we are done with training, we can use our network to detect the objects in Minecraft while the game is running. Darkflow returns image detection results in a form of json array of json object. Each json object contains the information about the label of the object, its bounding box which is specified by the coordinate of the top left corner and the coordinate of the bottom right corner, confidence level of prediction. We extract this information to find the center of the bounding box around the target object that we are most confident about and then move the agent's aim towards that pointand then shoot an arrow at the target.
## Evaluation
## References
[Image Processing](https://github.com/jennyzeng/Minecraft-AI)
<br />
[Image Labeling software](https://github.com/tzutalin/labelImg)
<br />
[YOLO: Real-Time Object Detection (Tensorflow)](https://github.com/thtrieu/darkflow)
<br />
[YOLO: Real-Time Object Detection (C)](https://pjreddie.com/darknet/yolo/)
<br />
[Project inspiration](https://www.youtube.com/watch?v=4eIBisqx9_g&t=444s)