# **Finding Lane Lines on the Road** 

The goal of this project is to build a pipeline to detect lane lines on the road from video using Python and OpenCV.

![](https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_images_lines/solidYellowCurve2.jpg)

---

## Description

My pipeline consists of the 9 following steps:

- **Change color space from RGB to HSL, and select colors (yellow and white only)**
> NOTE: Added to overcome low-contrast situations (see [challenge](https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_videos/challenge.mp4) video)

<img src="https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_images_color_selection/solidYellowCurve.jpg" width="480" alt="RGB to HSL and colors selection" />

- **Convert images into grayscale**

<img src="https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_images_gray/solidYellowCurve.jpg" width="480" alt="Converted into grayscale" />

- **Apply a Gaussian blur**

<img src="https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_images_blur_gray/solidYellowCurve.jpg" width="480" alt="Gaussian blur" />

- **Detect edges using Canny edge transform**

<img src="https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_images_edges/solidYellowCurve.jpg" width="480" alt="Canny edge" />

- **Mask part of the images outside of the region of interest for lines finding**

<img src="https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_images_masked_edges/solidYellowCurve.jpg" width="480" alt="Region of interest" />

- **Use Hough transform to find the lines**

- **Separate left lines from right ones and filter by slope boundaries**
> NOTE: Slope boundaries added to get rid of 'outlier' detected lines

- **Fit a single straight line and smooth the result by taking into account the 10 previous images**
> NOTE: Uses least square polynomial fit from numpy. Previous lines slope/intercept memorized to overcome sudden changes between images.

- **Draw the lines on top of the original image**

<img src="https://github.com/gdangelo/CarND-LaneLines-P1/blob/master/test_images_lines/solidYellowCurve.jpg" width="480" alt="Region of interest" />

The output for each step is saved in the following directory for single image:

- [test_images_color_selection](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_images_color_selection)
- [test_images_gray](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_images_gray)
- [test_images_blur_gray](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_images_blur_gray)
- [test_images_edges](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_images_edges)
- [test_images_masked_edges](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_images_masked_edges)
- [test_images_lines](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_images_lines)

And in the following directory for the videos: [test_videos_output](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_videos_output)

## Potential shortcomings and improvements

One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...

A possible improvement would be to ...

Another potential improvement could be to ...
