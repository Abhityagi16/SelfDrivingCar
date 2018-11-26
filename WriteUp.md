# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
1. Convert the image to grayscale
2. Use Gaussian Blur to smoothen the image
3. Detect edges using Canny algorithm
4. Mask the region containing lane lines 
5. Run Hough Transform algorithm to draw lines

After these steps I combined the image received from Hough Transform Algorithm with the original image to get the desired image with lane lines highlighted.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. First I calculated the slope of all lines. If slope of a line is negative then it is part of left lane and if it is positive then it is part of right lane. After collecting the slopes of all lines, I calculated the mean of left lane line slopes and right lane line slopes. After calculating the slope, I used the equation `y = mx + c` to calculate the intercept. I did the same process for right line as well. Then I drew the line using mean slope and intercept on both lane lines.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there is a road turn in the image. Currently the algorithm only works for straight road.

Another possible shorcoming could be when there is a slope on the road. We have hardcoded the region to be mask in 4th step. In case of slope this region would be different.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use a curve instead of straight line to define the lane lines

Another potential improvement could be to use better algorithm rather than simple averaging and extrapolating lane lines.