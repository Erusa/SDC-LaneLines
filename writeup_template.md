# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)
[image1]: ./writeup_picture/download.png "P1"
[image2]: ./writeup_picture/download%20(1).png "P2"
[image3]: ./writeup_picture/download%20(2).png "P3"
[image4]: ./writeup_picture/download%20(3).png "P4"
[image5]: ./writeup_picture/download%20(4).png "P5"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps:

0. A Gray Picture is created, which would be at the end of the pipeline only the two searched lines
1. This Picture is filtered with Gaussian blur, using a kernel of size 5.
2. Here, Canny function is applied in order to get the edges of the Image. 
3. By driving a car, the road (lines on the road) will be at certain position. This position is observed in the images and a region of interest is extracted from Picture. Other areas are just deleted from the picture.
*Short comming: Region of interes is defined with a fix value. However, it would change depending on the road (inclination of the road, country, ...)*
*Suggestion: One function should be created to give the region of interest, which use information such as country, first frames, car model, ...*
4. From the remaining information on the picture, while using Hough Line Theory, lines on the picture are computed
5. Now the lines are joined to form only two lines. For that **draw_linesOpt()** function is used, which analyzed all the previous lines and decide if they should be used for right or left line, or also just be ignore (noise). Fo the decision, an acceptable slope and acceptable X position are given.
*Short comming: Acceptable X position is a fix value.*
*Suggestion: This values should depend on the region of interest, and be updated based on the road*



. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
