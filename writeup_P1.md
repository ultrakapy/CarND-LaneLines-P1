# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on my work in this written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteRight_Out.jpg "Solid White Curve"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale, then I ran gaussian blur, canny edge detection, and defined the region of interest. I then ran the masked edges from the region of interest the hough_lines method and finally ran the weighed_img method on the result of hough lines and the inital image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
* Separating the left line segments from the right ones by calculating their slopes and examining the sign. The left lines have a negative slope and the right lines have a positive slope.
* For each lane line, I calculated the average slope of the line segments.
* Then I used the formula for a linear line, Y = MX + B, to calculate starting and ending points for the extrapolated lines in the region of interest.

Here are an example image of the output of my pipeline code: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when a white car or other white object enters the region of interest and they are incorrectly detected as lane lines.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to smooth the extrapolated/average lane lines that are drawn. Right now they change slightly from frame to frame.

