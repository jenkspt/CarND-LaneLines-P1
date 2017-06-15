Finding Lane Lines on the Road
--------------

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/solidWhiteCurve.jpg "Grayscale"
[image2]: ./test_images_output/SolidYelloCurve.jpg "Grayscale"
[image3]: ./test_images_output/whiteCarLaneSwitch.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
1. Convert to grayscale
2. Apply Gaussian blur
3. Detect edges with Canny Edge detection
4. Select area of interest
5. Use the Canny Edge output in a probablistic Hough Transform to find lines
6. Draw lane lines

In order to draw a single line on the left and right lanes, I modified the `draw_lines()` function 
to classify each line as a left lane line or a right lane line based on its slope. 
Using the lines in each lane line, I derived a formula for each lane line by taking the weighted 
average of each of the individual line segment coefficients, using the length of the line segment 
as its weight. I added a parameter for a minimum y value for each line to limit the distance the
lines extend into the horizon.

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

There is at least one frame of the video where no lines are detected. Also 
using a cartesian equation for the lines disallows vertical lines. It is also
unlikely that this lane detection pipeling would be robust varying road conditions.


### 3. Suggest possible improvements to your pipeline
computing the weighted average of the line coeficients over time would improve the smoothness and 
reliability of the lane detection, as would replacing outliers with the previous frame.

Since the lane lines have a well defined shape, and the direction of the vehicle is somewhat predictable,
the search space could be reduced significantly which would reduce the possibility of detecting lines 
which are not lane lines.

