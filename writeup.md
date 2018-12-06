# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


![alt text](/examples/grayscale.jpg)
![alt text](/solidWhiteCurve_find.jpg)
![alt text](/solidWhiteRight_find.jpg)
![alt text](/solidYellowCurve2_find.jpg)
![alt text](/whiteCarLaneSwitch_find.jpg)


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

1.Using slope = (y2-y1)/(x2-x1) to find the slope of each segment of lines found by Hough Transformation

2.We can then easily figure out that slope is < 0 it is on the left lane if it is > 0 it is one the right lane

3.We could then use a reasonable range of slope for right lane and left lane respectively to include lines that one the right_lane =\[]  and on the left_lane= \[]

4.We could use slope within \[-0.6,-0.9] as identifying points on the left lane and slope within\[0.5,0.7] as points on the right lane, for points that satfisfy the slope range will be stored in the right_lane and left_lane respectively

5.Now we have all the right points that we need to construct the whole line on right and left lane.We could use the np.polyfit(right_lane_x,right_lane_y,1) to find out the best line that fit all the points on the right lane.

6.Then we just need to find the intersection of the points of this line with top and bottom point of the area that we are interested in.

7.We draw such two line left lane and right lane on the image




### 2. Identify potential shortcomings with your current pipeline

Since we use the reasonable slope to find the points in the right lane and left lane ,but sometimes, the slope could be hard to define , for example , when there is turninig point like the one in the chanllenge excercise ,this method would not work.


### 3. Suggest possible improvements to your pipeline
if there is curvature ,the lane stay relatively straight in the "near sight" we possibily we could "shrink" the area of interest to more of the bottom of the image and identify the lines and fit from there


