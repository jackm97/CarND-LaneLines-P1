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

My pipeline consisted of 5 steps:

1. Set white pixels to and yellow pixels to (255,255,255) to better differentiate lanes from the road
2. Changed the image to gray scale
3. Blurred the image
4. Used Canny edge detetection to identify edges
5. Used a region mask to only include the car's lane
6. Used the Hough detection algorithm to draw lane lines

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by including a global called cache that records the slope and intercept of the left and right lanes from the previous frame. To separate the lines from the left and right side of the lane I found the slope of each line and if it was negative it was on the left and if it was positive it was on the right. From there I performed a weighted average of the slopes and intercepts from the current frame and previous frame. With these slopes and intercepts I found the endpoints to draw the single line for the left and right side.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when lanes are poorly painted. 

Another shortcoming could be what would happen when there are glares from the sun on the lens of the camera (i.e. sunset).


### 3. Suggest possible improvements to your pipeline

A possible improvement could be to super impose a portion of the lines from the previous frame instead of just the slope to help the algorithm with frames where it has a hard time detecting lines
