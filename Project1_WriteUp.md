# **Project 1 Finding Lane Lines on the Road Write-up** 
The goals of this writeup are the following:
* Describe the pipeline I made for finding the lane lines on the road.
* Reflect on the project 1. 


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 9 steps as I also annotated in the code:
First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...

Current pipeline does not utilize color selection method

### 3. Suggest possible improvements to your pipeline

1. A possible improvement would be to include cv2.inRange() for color selection so the pipeline could identify not only right left lane but also the white or yellow line. For regulation/ obey traffic law purpose, this could be quite useful.

Another potential improvement could be to ...

