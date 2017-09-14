# **Project 1 - Finding Lane Lines on the Road** 

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

### 1. Pipeline

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Shortcommings

My pipeline fails to perform well when there is reduced contrast between lane line and the road surface. Concrete road surfaces are lighter than tar and resulting in reduced contrast making it harder to detect the lines.

Shadows on the road are incorectly pick up by the 

Curved Lines

No line on left or right

Other vechiles on the road could obstruct the lines

Construction and missing lines


### 3. Improvements

Some improvements were made to address some if these issues. The graddient of the lane lines is about 45deg most of the time so lines that are mnore horizontal are filtered out. This helps reduce the 

Another potential improvement could be to ...
