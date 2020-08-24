# **Finding Lane Lines on the Road** 


## Pipeline description

The following pipeline consists of 7 main steps:

1- Conversion of the images to grayscale. 

2- Extraction of the edges using the Canny Edge algorithm.

    low_threshold = 50, high_threshold = 150

3- Selection of the the image section belonging to the road (assuming that the camera is placed on the top center of the car). 

    Vertices: [400,350],[600,350],[900,540],[150,540].

4- Hough transofrm of the selection.

    rho = 2; theta = pi/180, threshold = 10, min_line_length = 20, max_line_gap = 5

5- Separation of the left lines from the right ones (paying attention to not consider the flat lines).

6- Average of slope and intercept of the left and right lines 

7- Weighting funcion between the parameters of the detected lines in the previous frame and the ones detected in the current frame (weight = 0.3).


## Potential shortcomings


One potential shortcoming would be in case the lane lines are outside the region of inerest (for example during a steering maneuver).

Another shortcoming could be in case of low or visibility partially occluded.

In addition, other vehicles inside the region of interest might cause false detections.


## Possible improvements

A possible improvement would be to make the pipeline more robust to any video disturbance (sun, rain, fog, dirty camera lenses,...) and road disturbances (potholes, other vehicles,...)
