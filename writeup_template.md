#**UKF Project** 

##Writeup Template

---

**Implemented and used an Unscented Kalman filter for tracking non-linear motion**

The goals / steps of this project are the following:
* Implement Unscented Kalman filter to track a non-linear motion of an object, a bicycle in this case
* Compare the fused data (from both radar and laser) with an individual sensor.
* Compare RMSE result of this non-linear motion with an Extended Kalman filter result obtained earlier

## Rubric Points
###Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/783/view) individually and describe how I addressed each point in my implementation.  

---
####1. px, py, vx, and vy RMSE should be less than or equal to the values [.09, .10, .40, .30] for data from simulator for fused data

* For fused data(both radar and laser) I received a result of
    px = 0.0663
    py = 0.0888
    vx = 0.3245
    vy = 0.2395

* Also RMSE for fused (radar + laser ) is lower than individual Laser or radar RMSE.
  Can be on or off by toggling the flag   "use_laser_" or "use_radar_"

####2. Your algorithm should use the first measurements to initialize the state vectors and covariance matrices.

* This is done in file ukf.cpp inside UKF method ProcessMeasurement(), inline comments include detail description and assumption.

####3. Upon receiving a measurement after the first, the algorithm should predict object position to the current timestep and then update the prediction using the new measurement.
####4. Your algorithm sets up the appropriate matrices given the type of measurement and calls the correct measurement function for a given sensor type


* This is done in file ukf.cpp inside UKF method ProcessMeasurement(), a predict() is followed by sensor specific measurement update.

####5. Compare your UKF and EKF project results. Both projects use the same data file. RMSE, especially for vx and vy should be lower for the UKF project than the EKF project

Result for EKF was 
px = 0.0944
py = 0.0848
vx = 0.3883
vy = 0.4237

RMSE for ukf is lower than ekf.

#### Visualize NIS Data

//]: # (Image References)

[image1]: ./visualization/nis_plot_radar.png "NIS plot, data from Radar only"
[image2]: ./visualization/nis_plot_laser.png "NIS plot, data from laser only"
[image3]: ./visualization/yaw_radar_laser_vs_time.png "Yaw plot, from fused data"
[image4]: ./visualization/yaw_rate_radar_laser.png "Yaw rate plot, from fused data"
[image5]: ./visualization/yaw_vs_time_laser_only.png "Yaw plot, from laser only"
[image6]: ./visualization/yaw_rate_laser_only.png "Yaw rate plot, from laser only"
[image7]: ./catch_car/Catch_car.png "Yaw rate plot, from laser only"

My test results have been save in file 
   obj_pose-laser-radar-ukf-output.txt  -->  for rader and laser 
   obj_pose-laser-only-ukf-output.txt   -->  for laser only

the python script to draw the data is in file ukf-visualization.ipynb

1. Figure for NIS Data from radar with time k is presented in
   fig: "NIS vs measured time"  where 95% line (7.8) is also drawn.
   It matches the expectation, there are few peaks (<5%) above 7.8
   ![alt text][image1]
   Similarly NIS data for laser is also drawn and match the expectation.
   ![alt text][image2]
   
2. Ground truth and estimated yaw and yaw rate with time is also drawn for fused data
 ![alt text][image3]
 ![alt text][image5]
 ![alt text][image4]
 ![alt text][image6]
 
 I have also completed the Bonus challenge.The code is placed under Catch_car folder and the result of the project is mentioned below:
 ![alt text][image7]
 
