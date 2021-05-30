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

### Reflection of my First Pipeline, using draw_linesOpt()

My pipeline consisted of the following steps:

0. A Gray Picture is created, which would be at the end of the pipeline only the two searched lines
1. This Picture is filtered with Gaussian blur, using a kernel of size 5.
![alt text][image1]
2. Here, Canny function is applied in order to get the edges of the Image. 
![alt text][image2]
3. By driving a car, the road (lines on the road) will be at certain position. This position is observed in the images and a region of interest is extracted from Picture. Other areas are just deleted from the picture.
![alt text][image3]
*Short comming: Region of interes is defined with a fix value. However, it would change depending on the road (inclination of the road, country, ...)*
*Suggestion: One function should be created to give the region of interest, which use information such as country, first frames, car model, ...*
4. From the remaining information on the picture, while using Hough Line Theory, lines on the picture are computed
![alt text][image4]
5. Now the lines are joined to form only two lines. For that **draw_linesOpt()** function is used, which analyzed all the previous lines and decide if they should be used for right or left line, or also just be ignore (noise). For the decision, an acceptable slope and acceptable X position are given. Then, cv2.fitline function is used to each of the two lines.
*Short comming: Acceptable X position is a fix value.*
*Suggestion: This values should depend on the region of interest, and be updated based on the road*
![alt text][image5]

The result of this pipeline gives a good recognition of the two given videos. However, lines oscillate two much.


### Reflection of my Second Pipeline, using draw_linesOpt2()
Here almost the same pipeline as the previous one is used, also the short comming and suggestion are still valid.

The goal of my second Pipeline was to reduce the oscillation of the lines, by using the information the old frames. Because of that, the function draw_linesOpt() is replaced by draw_linesOpt2():
5.1 I defined 6 global variables: the slope, start point and end point of right and left line. This value represent the average of the 7 last frames lines.
5.2 Using the same method as the previous pipeline, the expected two lines for certain frame are computed
5.3 Now, an average of this two lines with the information of the last 7 frames lines are calculated. 
*Short coming: Initial value for global variables only came from first frame.*
*Suggestion: First frames should be used not to draw lines, but to define **aceptable** values, also detecting and ignoring misleading information. 
*Short coming: It would slow also needed changes. If a wrong line is identify, it would remains on the average*
*Suggestion: Mean should be used, not average*





One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
