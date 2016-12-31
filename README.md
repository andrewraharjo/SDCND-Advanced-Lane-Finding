# SDCND-Advanced-Lane-Finding

The goals / steps of this project are the following:

* Compute the camera calibration matrix and distortion coefficients given a set of chessboard images.
* Apply the distortion correction to the raw image.  
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view"). 
* Detect lane pixels and fit to find lane boundary.
* Determine curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and numerical estimation of lane curvature and vehicle position.

---

The images for camera calibration are stored in the folder called `camera_cal`.  The images in `test_images` are for testing your pipeline on single frames.  The video called `project_video.mp4` is the video your pipeline should work well on.  `challenge_video.mp4` is an extra (and optional) challenge for you if you want to test your pipeline.

If you're feeling ambitious (totally optional though), don't stop there!  We encourage you to go out and take video of your own, calibrate your camera and show us how you would implement this project from scratch!


The main areas where this pipeline could be improved are the following:

1) Given 20 calibration images from camera_cal images. I'll consider to get more calibration images. This will help to improve the distortion correction.

2) Leveraging from ROI (color selection and region masking) P1, I use the red channel threshold for color selection. Basic CV implementation needs to be extended to figure the color of lines and pavement. One of the thing I could improve is the shadow the color selection.

3) For gradient selection, I use Sobel X Threshold. Increasing kernels might give improvement for this step. One thing for sure, we can create a UI based type to test the transfromation.

4) I did hardcode the perspective transform. When I try to run it with the challenge video, the result changes and it affects the measurement of the curvature and position. I'd explore with different persfective transform to figure the angle of vehicle, let's say use another sensor data like AHRS/RTK/GNSS and IMU.

5) The perspective transform is hardcoded at this point. When the vehicle bounces or the road is not a flat surface, the result changes, which will affect the measurement of curvature and position. Having a dynamic perspective transform that is based on some knowledge of the pitch angle of the vehicle (IMU measurement for example) could improve this step.
