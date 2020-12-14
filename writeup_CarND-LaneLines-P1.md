# **Finding Lane Lines on the Road** 

## Writeup


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Pipeline description.

The pipeline consisted of 5 steps. The pipeline process one image at time. Image can come from a folder or a video

1- Garyscale conversion;

2- Gaussian filtering;

3- Canny fuction for edges identification;

4- Mask creation

5- Hough parameters setup and Hough transformation;


draw_lines() in HoughLinesP function description:


1- For each set of coordinates found in HoughLinesP() output, slope and center coordinate (x,y) are calcualted;

2- Set of parameters 'epsilon' are defined and used as in the following step;

3- If slope value is between 'epsilon_pos' and 'epsilon_pos_2', the slope and related center coordinates are classified as 

positive (right line), otherwise are classified as negative (left line);

4- Mean avergae of positive/negative slopes and center coordinates (position) are calculated;

5- Y coordinates are obtained by vertices used for mask creation and adapted to the final line shape;

6- X coordinates are extrapolated from:

X(1,2)_(right,left) = 1/(r,l)_slope*((r,l)_slope*(r,l)_center[0] - (r,l)_center[1] + Y(1,2)_(right,left)) 

where (r,l)_center[] is a list of center coordinates (x,y) for right and left respectively.


### 2. Shortcomings with current pipeline

- The code is not robust enough to work with complex videos that include different asphalt colour.

- There is no cache containing previous picture information (slope and center coordinates) to be used as set of data for a more 

efficient classification.

### 3. Possible improvements to pipeline

- Cache list of previous picture information for more efficient classification.

- Tool implementation for live parameters tuning.
