# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I added gaussian blur to the images. Next canny edge detection was used to find edges. A region of interest in the shape of a traezoid was selected in the video to eliminate edges that were not part of the road. Next 
Hough transform was used to detect lane lines. 


In order to draw a single line on the left and right lanes, I modified the draw_lines() function. I named it draw_lines_modified. For each of the lines detected I segregated the lines according to left line and right line based on the slope. Each line was given a weight according to the length of the line. Finally a weighted average was calculated to find the slope and intercept of the line. Given the slope and intercept I then drew lines with y_max to the bottom of the image and y_min to a chosen desired point. This was done for both the left and right lane. 


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there is curvature in the road. The average function wont be able to fit for the curvature. 

Another shortcoming could be differnt lighting conditions. The houghs transform is tuned for particular images. It may not work for different lighting conditions. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to fit polygons instead of straight lines to the lane lines. 

Another potential improvement could be to use other filters to robustly detect lane lines. 
