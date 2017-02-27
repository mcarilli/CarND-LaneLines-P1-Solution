#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps:
* 1. Construct a filter that removed pixels that were not close in color to white or yellow.
* 2. Convert the image to grayscale.
* 3. Gaussian-blur the grayscale image with a kernel size of 5.
* 4. Run Canny edge-detection on the blurred image, with low and high gradient thresholds of 50 and 150 respectively.
* 5. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline

1.  My pipeline relies on a tightly restricted region of interest based on trial and error with the given images.  The advantage of this approach is that it reduces environmental clutter, but the disadvantage is that the car must remain well-centered within the lane.  If the car begins to deviate from the lane, it must correct quickly, or else one lane line will disappear from the masked region and cease to be detected.

2.  If a white or yellow car cuts directly in front of my car and begins to occupy a large part of the region of interest, I expect we are screwed.  I assume that later in the course we will develop methods to recognize and respond to other cars.

3.  My scheme for separating yellow and white lane lines from the background road fails on the variably-lit road present in the challenge problem.  I need to figure out a better way to identify white and yellow pixels. 

###3. Suggest possible improvements to your pipeline

The tight-region-of-interest approach is not terrible, because that region of interest appears fairly consistent across samples, and should remain so as long as the car drives precisely.

For now, my top priority is to figure out a better way to identify white and yellow pixels on a variably-lit background.  Perhaps color information could be combined with some information from nearby pixels to tag pixels with "relatively" high yellowness or whiteness compared to the local background.

