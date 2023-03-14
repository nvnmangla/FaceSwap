# FaceSwap
The aim of this project is to implement an end-to-end pipeline to swap faces in a video just like Snapchat’s face swap filter.
## Phase 1: Traditional Approach 
### Algorithm
This phase include the Traditional way of swapping faces.
We will provide details of our approach for two faces in a
single frame and two different faces in two different frames.
We then extrapolated our results to videos by computing them
frame by frame. The steps are as follows

- Extracting Landmarks 
- Warping 
- - Delaunay Triangle 
- - Thin Plate Spline 
- Blending (Contrast)

#### Extracting Landmarks 
For this section. We computed 68 landmarks for each face
provided by [Dlib](https://pyimagesearch.com/2017/04/03/facial-landmarks-dlib-opencv-python/) library built into OpenCV and python. 

<figure>
  <img src="https://github.com/nvnmangla/FaceSwap/blob/master/Images/face.png" alt="Landamakrs- single frame"/>

  <figcaption align='center'>Landmarks for Two faces in Single frames.</figcaption>
</figure>
<!-- 
![Landmarks single frame](https://github.com/nvnmangla/FaceSwap/blob/master/Images/face.png)*Landmark single frame*
 -->


<!-- The first step in the traditional approach is to find facial landmarks (important points on the face) so that we have one-to-one correspondence between the facial landmarks. For detecting facial landmarks we’ll use dlib library built into OpenCV and python. We then warp the faces using the **Triangulation** and the **Thin Plate Spline (TPS)** methods. -->

## Phase 2: Deep Learning Approach
In this phase, we run an off-the-shelf model of the Position Map Regression Network (**PRNet**) to obtain full face fiducials, which implements a supervised encoder-decoder model to obtain the full 3D mesh of the face.

## Instructions to run the code
- Firstly please download the model for landmarks model for Phase 1 from [GoogleDrive] https://drive.google.com/file/d/1tY3nw20LgUbknVx2AMTwLG6QNZG93E1H/view?usp=sharing and put it into Code/Phase1
- Then, download the PRN trained model from [GoogleDrive] https://drive.google.com/file/d/1UoE-XuW1SDLUjZmJPkIZ1MLxvQFgmTFH/view, and put it into Code/Phase2/Data/net-data

The final script is split into two parts : Wrapper_P1.py and Wrapper_P2.py.
Wrapper_P1.py contains the code belonging to Phase 1 (Triangulation and Thin Plate Spline methods) and Wrapper_P2.py contains the code for Phase 2 (PRNet model).

To execute Phase 1:
* cd to the directory where the package is located 
* Enter the following into the terminal: python Wrapper_P1.py InputFilePath _ InputFileName _ RefFileName _ Method _ SaveFilePath _

To execute Phase 2:
* cd to the directory where the package is located 
* Enter the following into the terminal: python Wrapper_P2.py InputFilePath _ InputFileName _ RefFileName _ SaveFilePath _
