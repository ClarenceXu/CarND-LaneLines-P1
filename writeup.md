# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidYellowCurve.jpg "solidYellowCurve"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. 
1. Select color white and yellow from the image
2. Convert the images to grayscale
3. Use Gaussian blur to reduce detail  
4. Use canny to identify the edage 
5. Define the region_of_interest 
6. Detect the lines using hough transformation

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
1. Catogorize left and right line segments
2. Remove noise lines based on the slop of the lines, e.g. slope of a right lane shall large than 0.5, slope of a left lane shall smaller than -0.5
3. Calculate the average slope and middle point of left and right line segments 
4. draw left and right lanes using the average slope and middle point

Here is an example after using the pipeline:
![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be the marked lanes will not be accurate when the lane has a sharp curve.

Another shortcoming is that when the color of the lane changes, e.g. shadowed, the lane could not be detected. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to find a better way to extrapolate the line segments.
I simply averaged the slop of detected left or right segments, calculated the middle point by averaging all the start/end points of line segments. A better transformation based on these line segments should be implemented. 

Another potential improvement could be to find a better way to identify the best parameters' combination for gaussian blur, canny and hough transformation. I manually tested different combination and check which one has the best result.  It is better to find a more intellegent approach.
