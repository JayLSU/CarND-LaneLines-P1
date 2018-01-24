# **Finding Lane Lines on the Road** 

## Writeup Report for P1

---

**Project 1: Finding Lane Lines on the Road**

The goals of this Project 1 is using computer vision techniques to find the lane lines in good and simple conditions. Through the examples, I have learned how to effectively find out the road lane lines in simple cases. However, through the running of the challenge video, I noticed that the techniques learned in project 1 is not enough. The details will be inclued in shortcoming section.



[//]: # (Image References)

[image1]: ../test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"

[image2]: ../test_images_output/solidWhiteRight.jpg "solidWhiteRight"

[image3]: ../test_images_output/solidYellowCurve.jpg "solidYellowCurve"

[image4]: ../test_images_output/solidYellowCurve2.jpg "solidYellowCurve2"

[image5]: ../test_images_output/solidYellowLeft.jpg "solidYellowLeft"

[image6]: ../test_images_output/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"

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

![solidWhiteCurve][image1]

![solidWhiteRight][image2]

![solidYellowCurve][image3]

![solidYellowCurve2][image4]

![solidYellowLeft][image5]

![whiteCarLaneSwitch][image6]

You can also check the video outputs in [test_videos_output](../test_videos_output).

### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming would be when the color of lane lines are not quite clear under the road background. Just as shown in challenge video. Since the contrast of lanes and road background color are limited, the edges of the lines can not be identified and detected. 

Another shortcoming could be bad detecting performance in dark turnnels or low light condition or bad weather condition, which will also leads to bad detection of road lanes. 

One more shortcoming could be the line detection and drawing for shraply curved road lanes. 

I modified draw_lines() by groupding different lines into left and right lines according to their slopes. 
To avoid slope to be infinity and increasing nonlinearly, I transformed the slopes in radius unit. Since I assumed that the car was always in the middle of the lane and camera was fixed, so the lanes slopes should be in two major ranges, one for left and one for right. Through analyzing the slopes in the example images, I set two thresholds for slope detection in my code (0.7 and 0.5) to exclude too vertical lines and too honrizontal ones. In this method, we can avoid some outliers lines in the selected area and properly draw lines on the original lanes. In fact, if the car is not the middle of the lanes, the slopes could exceed my thresholds. To develop a dynamic method to find out the major slopes in different ranges, more complexed method could be used. For example, we can divided 0 to pi/2 into 10 pieces, then use counter to identify the most one, that usually would be the detected lane lines' slopes. Therefore, we can exclude outlier lines in the selected area, which could be detected old lane lines, some stickers, or tree branches.

### 3. Suggest possible improvements to your pipeline

A possible improvement for the first two shortcomings could improve the contrast of the image which may enhance the identification of lanes. Or use other color space to extract the lane lines from the image, for example HSI image space, HSV image space, and maybe something else.

Another potential improvement for the third shortcoming could use calculate some offset for line drawing and according to the offset, draw curved lines instead of straight lines when necessary.
