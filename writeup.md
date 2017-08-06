# **Finding Lane Lines on the Road** 

The goal of this project is to build a pipeline to detect lane lines on the road from video using Python and OpenCV.


![solid-white-right-line](https://user-images.githubusercontent.com/4352286/29003803-e2a66b26-7abd-11e7-8c87-f60e7d80b5e2.gif) | ![solid-yellow-left](https://user-images.githubusercontent.com/4352286/29003804-e2a6e614-7abd-11e7-84d2-36cbf7594f7f.gif) | ![challenge](https://user-images.githubusercontent.com/4352286/29003805-e2a70978-7abd-11e7-88c5-62f3da4c6ab3.gif)
--- | --- | ---

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

## Potential shortcomings

This simple lane lines finding process is optimized for the test videos provided only. All the parameters have been tuned according to the 3 videos in [test_videos](https://github.com/gdangelo/CarND-LaneLines-P1/tree/master/test_videos). 

Hence, it will not generalize well for unseen roads such as steep roads, or roads with bends. Indeed the process can only handle straight lines with fixed length within a fixed region of interest. 

Furthermore, I didn't test the algorithm against different weather conditions or with dense traffic. As all the computer vision steps (canny edge, hough transform...) have been tuned with the test videos only, I believe it won't perform well under the rain.

## Possible improvement

A possible improvement would be to further tune the parameters of the current process to get rid of the shakiness of the lines drawing. However, a great improvement would be to handle steep roads and bends on any roads and conditions. In this case, the algorithm has to be rethinked, in particular for the lines drawing that fit straight line only. 
