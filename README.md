# Panorama Project

This is a Python 3 based Panorama Project.

## Explain
In this project, we want to create a physical space display by several images.

Gets a sequence of images, and find the matches points between the images, and the way of the image display and stitch them into one panorama image.

## The code
My script uses OpenCV to first calculate the SIFT keypoints with the 2 best matches and filter by 0.5 ratio, between 2 images. Those keypoints are passed into a ```ransacHomography``` function that then calculates a homography and inliers. ```ransacHomography``` will choose four random correspondences, calculate a homography, by using ```leastSquares``` algorithm to find the homography, collect the inliers, and keep the inliers they more than any inliers yet found, in the end compute again the homography with all the inliers to get the exact homography. There is also a threshold parameter for the function that takes a number that defines a limit where a key points is considered appropriate for homography, and number of rotations for searching the most inliers.
The inliers and outliers can be displayed between 2 images using the ```displayMatches``` function. the matching points will be shown in red, the outliers will be shown in blue and the inliers will be in yellow.
The homographies are then converted to a common axis system for stitching the images using the ```accumulateHomographies``` function.
Then each color channel is stitched with all the images, each image according to its corresponding homograph, by the ```renderPanorama``` function.

## Author
Omer Edut
