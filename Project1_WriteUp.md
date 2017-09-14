# **Project 1 Finding Lane Lines on the Road Write-up** 
The goals of this writeup are the following:
* To describe the pipeline I made for finding the lane lines on the road.
* To reflect on the project 1 by discussing the shortcomings and the possible improvements on the current pipeline. 


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps as I also annotated along with the code in P1 notebook:

* Step 1. Convert the image to grayscale by applying Grayscale transform 

* Step 2. Reduce image noise by applying Gaussian smoothing

* Step 3. Convert the grayscale image to the edges image (dots) by applying Canny edge transform

* Step 4. Limit the region of interest (ROI) to be only on te road by using the helper funciton- cv2.fillPoly to create a masked image

* Step 5. Convert the edges detected image from image space (points) to Hough space (lines) and draw those lines out


Here I improved the draw_lines() function by doing the following:

 a) From those lines I got after the hough transform, I calculate their slopes and only take those lines with the slope in the range I desired, here I give it the range from 0.4 to 2.2. It will reject those hough lines that are being too flat or too vertical, which are considered as noise as this point.  
 
 b) From the calculated slopes, I could also separate those hough line segments into two catagories: left lane lines (positive slope) or right lane lines (negative slope). 
 
 c) Then in each catagory I averaged each line segments (y=mx+b) by averaging their slope(m) and the intercept(b). The averaging takes length of Hough line into consideration, longer lines has higher weight, i.e. longer lines weight in more than shorter lines.   
   
   
* Step 6. Final step is to put those semi-transparent left and right lines into the original image by using the helper function cv2.addWeighted. 




### 2. Identify potential shortcomings with your current pipeline
Potential shortcomings with the current pipeline are:
* Canny edge detection rely on the gradient (color change) of the image in order to identify the edge, that mean when the color of the road is light, or close to color of the lane lines (yellow or white), the whole line detection would be shaky. This shortcoming is quite obvious in the challenge video between 0:03 - 0:05 when the road color is relatively light and the averaged/extrapolated lines become way off (comparing to when the road color is dark).

* Comparing to detecting the solid line, current pipeline shows lower detecting performance on the dash lines (1st video 0:02-0:03)



### 3. Suggest possible improvements to your pipeline

Several possible improvements are identified:

* To continue tuning the parameters in Canny edge detection algorithm and Hough transform algorithm for a better edge (points/dots) and hough lines detection. 

* To adjust the masked image area (vertices) due to the lane lines are much more close to the right in the Optional Challenge video.

* To include cv2.inRange() for color selection so the pipeline could identify not only right left lane but also the white or yellow line. For regulation/ obey traffic law purpose, line color identify could be quite useful.



