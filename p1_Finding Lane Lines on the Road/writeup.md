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

My pipeline consisted of 5 steps. 

First, I converted the images to grayscale.

Then I applied Gaussian smoothing to the image.

The I applied Canny function to detect boundaries of the image

Then I used polyline to select the region of interest

Then I applied Hough transform to dectect the lines in the region of interest

Finally, I combined the detected lines with the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:

First, calculated the line slope and line intercept.

Then I removed the lines with slopes between -0.4~0.4, i.e. horizontal lines.

Then I spereated the lines to left/right by their slope (>0, right line, <0, left lines)

Then I averged the left lines (right lines) in to one single line.

Finally I extend the lines into the top/bottom of the region of interests.




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would a straight line dose fit well  when a line is in curve

THe pipeline also dose not work well when the road texture is complicated - it will detect too many lines, and the average line will be wrong.

It only decte the left and right line, while here are more lane lines on the road.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to only detect lines that are in yellow and white only.

Another potential improvement could be to ...
