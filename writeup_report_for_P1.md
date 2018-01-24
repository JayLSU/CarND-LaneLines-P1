# **Finding Lane Lines on the Road** 

## Writeup Report for P1

---

**Project 1: Finding Lane Lines on the Road**

The goals of this Project 1 is using computer vision techniques to find the lane lines in good and simple conditions. Through the examples, I have learned how to effectively find out the road lane lines in simple cases. However, through the running of the challenge video, I noticed that the techniques learned in project 1 is not enough. The details will be inclued in shortcoming section.



[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Pipeline Description.

My pipeline consisted of following steps:

* Firstly, transform a RGB image to a grayscale one.
* Secondly, use Gaussian Blur method to blur the grayscale image to suppress noise and spurous gradients.
* Thirdly, use Canny Edge Detection obtain the edges of the blurred image.
* Fourthly, apply a mask to select the region of interest.
* Fifthly, apply Hough transformation to find out the lines in the selected region of interest.
* Finally, draw highlighted lines on the original image.

I attach the output images of my pipeline process, whose inputs are 6 example images.



In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
