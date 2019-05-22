---
layout: default
title: Status
---
## Project Summary
Our Minecraft-AI project will focus on recognizing different characters in Minecraft such as Pig, Rabbit, Ozelot, Sheep, Cow and then try to attack the Pig. We will be using image detection to determine what animals are in the agent's view and where are they in the view. Based on the rule that we make, which is to attack Pigs, our agent will try to aim at a pig and shoot arrows at it. 
## Approach
## Evaluation
Since our project mainly focus on image detection, the performance of the project is measured by how accurately our object detector detects the animals. After we finish training our dataset, we will test our model on a set of 100 images that are generated from the game. The accuracy is the number of correct detections over the total number of objects. These numbers are counted manually.
## Remaining Goals and Challenges
For the remaining 2-3 weeks, we will try to improve the accuracy of our detector by training our neural network on a larger size dataset. At present, our network is trained on 400 images and has decent performance. The detector is able to detect more than half of the objects. We shoot for 1000 images in our training dataset.
Another thing that we need to do is implement the algorithm to aim at a target object. Darkflow provides an option to return the results of image detection in a form of JSON array. Each element in the JSON array is detected object. From that, we can determine where the target is then move the aim to aim at the target and the shoot at the target.
One limitation that we can think of is the overhead to load the agent's current view into the object detector. We need the detector to be able to detect the target in real time. If loading image takes too much time, the target might have already moved to a different place.
## Resources Used
[Image Capture](https://github.com/jennyzeng/Minecraft-AI)
<br />
[Image Labeling software](https://github.com/tzutalin/labelImg)
<br />
[YOLO Object Detection (You Only Look Once)](https://github.com/thtrieu/darkflow)

