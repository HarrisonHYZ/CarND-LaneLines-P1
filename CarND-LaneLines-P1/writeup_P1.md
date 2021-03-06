# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[pic1]: ./test_images_middle/solidWhiteCurve1.jpg "Grayscale"
[pic2]: ./test_images_middle/solidWhiteCurve2.jpg "Gaussian blurring"
[pic3]: ./test_images_middle/solidWhiteCurve3.jpg "Canny edge"
[pic4]: ./test_images_middle/solidWhiteCurve4.jpg "Interested area"
[pic5]: ./test_images_middle/solidWhiteCurve5.jpg "Draw line"
[pic6]: ./test_images_middle/solidWhiteCurve6.jpg "Original image with line"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 main steps. Firstly, I converted the images to grayscale(pic1). Secondly, I use the gaussian blurring to smooth the image to remove some unexpected noises(pic2). Thirdly, I use canny edge detection technique to convert the grayscale image to a black-white image with proper low and high thresholds(pic3). Then I define the triangular area which I am interested to only care about the lines in this area(pic4). Finally, I use the hough transform function to identify all the lines(pic5) and then draw the lines on the original images(pic6).

![pic1][pic1]
![pic2][pic2]
![pic3][pic3]
![pic4][pic4]
![pic5][pic5]
![pic6][pic6]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by differentiating the slope values. If the slope is bigger than zero, it is right line. Otherwise, it is a left line. With all the left and right lines and their corresponding points, I, firstly, remove the almost horizontal lines and then optimize the slope lists by removing the ones with big deviation from the average value. Finally, I use the average slope and a average (x,y) to find the intersections to find the upper point and the bottom point for left and right lines.

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be when the road line is not straight, the line will shake strongly on the video. The current algorithm cannot cover this situation well.

Another shortcoming is the red line on the original image is not very stable. Will be shaking a little bit all the time during the whole video.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use polyfit function to get the parameters for non-straight lines. Then I can draw the line which is not only straight, but also any shape.

Another potential improvement could be to optimize the code realization of all methods for the current strategy to make the code more concise.
