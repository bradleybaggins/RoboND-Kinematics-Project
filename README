## Project: Kinematics Pick & Place
### Writeup Template: You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

[//]: # (Image References)

[image1]: ./misc_images/misc1.png
[image2]: ./misc_images/misc3.png
[image3]: ./misc_images/misc2.png
[image4]: ./misc_images/URDF_sketch.jpg
[image5]: ./misc_images/DH_param.jpg
[image6]: ./misc_images/WC-Thetas123.jpg
[image7]: ./misc_images/WC-Thetas456.jpg
[image8]: ./misc_images/Transform.png
[image9]: ./misc_images/wrist_center.png
[image10]: ./misc_images/IK_orientation.png

## [Rubric](https://review.udacity.com/#!/rubrics/972/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.

You're reading it!

### Kinematic Analysis
#### 1. Run the forward_kinematics demo and evaluate the kr210.urdf.xacro file to perform kinematic analysis of Kuka KR210 robot and derive its DH parameters.

After inspecting the demo, I reviewed the KR210 urdf file to identify the DH parameters of the Kuka KR210 robot. This image shows the relative joints' relative positions and orientations.

![alt text][image4]

I created an outline of the table to house the DH parameters to transform the system from one joint to the next, and began to sketch out from one point to the next. This DH parameter table was populated after fitting lengths and angles to each piece.

![alt text][image5]


#### 2. Using the DH parameter table you derived earlier, create individual transformation matrices about each joint. In addition, also generate a generalized homogeneous transform between base_link and gripper_link using only end-effector(gripper) pose.

After visualizing and labeling the joint links and angles to create the modified DH parameter table, I created a formula to create a homogeneous transform matrix out of any given set of DH parameters. Using this formula, I applied each set of DH parameters as inputs and subs from the DH Table to generate each individual transformation matrix from one joint to the next.

![alt text][image8]

Using the roll, pitch, and yaw values of the end-effector, I built a rotational matrix in each plane to determine a combined rotational transform to the end-effector pose. After adjusting for the rotational error, the end-effector position and orientation values are substituted into the transform to identify the transform to the wrist center.

![alt text][image9]

![alt text][image6]


#### 3. Decouple Inverse Kinematics problem into Inverse Position Kinematics and inverse Orientation Kinematics; doing so derive the equations to calculate all individual joint angles.

And here's the derivation of the theta angles:

![alt text][image6]

![alt text][image10]

![alt text][image7]


### Project Implementation

#### 1. Fill in the `IK_server.py` file with properly commented python code for calculating Inverse Kinematics based on previously performed Kinematic Analysis. Your code must guide the robot to successfully complete 8/10 pick and place cycles. Briefly discuss the code you implemented and your results.


Here I'll talk about the code, what techniques I used, what worked and why, where the implementation might fail and how I might improve it if I were going to pursue this project further.

The code followed the order of the lessons and the guide fairly directly. First the symbols are initialized, the transformational matrices are built, rotation matrices are sliced from them to compute EE and Wrist center positions, and finally the theta angles are calcuated using inverse kinematics and some trigonometry.

I think the implementation has some lines it likely doesn't need, and a future implementation could probably make some decisions about the joint trajectories that are returned. I also wonder about how a different kind of implementation my request and evaluate poses.
