# Final project: Track 3D-Objects Over Time

## This project is about 3D object tracking based on Extended Kalman filter(EKF) approach using Lidar and camera measurements from the vehicle
### 1. In the first step EKF is implemented to track objects which are already detected through a deep learning approach resnet from Lidar measurements
the state vector of EKF includes 3D position and 3D velocity. the observation model here is a simple linear model as we get 3D position from lidar.
The result is following:

![track1](https://user-images.githubusercontent.com/125278855/227711996-1cc96abb-94cf-4bce-ac12-8b85fae73cf3.png)

### 2. In the second step track management is implemented to initialize a track state and covariance based on its first associated measurement then assign the track score. Additionally the transition between initialized, tentative, confirmed for each track was implemented choosing threshold on score and covariance values on x, y.
The following is the results of my experiments with two different threshold on track score for deletion of tracks. the first init threshold of 0.17 resulted not confirming any track:

![track1s2](https://user-images.githubusercontent.com/125278855/227712599-2e5eaa0c-d898-4bce-8285-ea63facf77b0.png)

![tracks22](https://user-images.githubusercontent.com/125278855/227712606-436b462a-0bba-4cf1-959a-5495ef73328d.png)

by choosing a lower threshold of 0.1 the result includes confirmed tracks:
![step2_t1](https://user-images.githubusercontent.com/125278855/227712650-df88228d-bce9-4937-ae98-28a8e5db3604.png)
![step2_t2](https://user-images.githubusercontent.com/125278855/227712655-c896040e-b23e-4f3f-bfe0-78e43fc2cc86.png)
![step2_rmse](https://user-images.githubusercontent.com/125278855/227712659-a37977f3-baf3-4adb-801e-debe0e0f7b11.png)

### 3. The third step is about association between tracks and measurements this was implemented based on Mahalanobis distance(MHD) using the covariance and residual between measurement and track state in addition to gating approach and simple nearest neighbor to pick the best association and remove the rest
The result is as following:

![step3_t1](https://user-images.githubusercontent.com/125278855/227713055-53fa58ee-2dc2-49a2-85c4-01a5d2c051a7.png)
the false positive detected objects are scored low in the following and later were removed by track management. tracks 1 and 2 are associated with the nearest measurements therefore new measurements can't affect.
![step3_t3](https://user-images.githubusercontent.com/125278855/227713061-5ea36535-ce6c-4e6a-aef2-e1d0e4c83009.png)
![step3_t4](https://user-images.githubusercontent.com/125278855/227713065-d4b2e771-4d29-42ed-b4ae-e41ae5512352.png)
![step3_t5](https://user-images.githubusercontent.com/125278855/227713071-1df68767-a848-4f73-9f4d-5c2133c75ac4.png)
![step3_t6](https://user-images.githubusercontent.com/125278855/227713073-25ec3472-7b34-4cf5-98d5-d8fabf539fa9.png)
![step3_t7](https://user-images.githubusercontent.com/125278855/227713076-4b8c802d-a1b4-42d2-b5e4-f6fe9c57d3f5.png)
![step3_t8](https://user-images.githubusercontent.com/125278855/227713081-bc81443b-078a-4a0c-9d56-db47145b100b.png)
![step3_rmse](https://user-images.githubusercontent.com/125278855/227713089-c5b97988-4fc8-4e00-abf8-026009775b8f.png)

### 4. Finally to improve tracking result camera measurement is fused using the same EKF and camera nonlinear measurement model. The nonlinear relation corresponds to transformation needed to converting between camera image and vehicle coordinate systems.
The result shows that using camera the RMSE is slightly improved for track one. also object 1, 2 are stably tracked during 185 frames used in this test.
![step4](https://user-images.githubusercontent.com/125278855/227714453-bebb6aef-c039-42bd-892e-ca0218de5705.png)
![step4_t1](https://user-images.githubusercontent.com/125278855/227714457-728be742-fbad-4865-af64-3fc67dbbfef4.png)
![step4_t2](https://user-images.githubusercontent.com/125278855/227714460-254253e6-3df2-4872-9e98-85d2069bb886.png)
![step4_t3](https://user-images.githubusercontent.com/125278855/227714467-c5f72911-a989-4517-9e49-c51c22059f3e.png)

A new track is initialized and associated correctly to a measurement 
![step4_t4](https://user-images.githubusercontent.com/125278855/227714469-87c58c76-75a4-403b-be8e-b05290be3bf6.png)
![step4_rmse](https://user-images.githubusercontent.com/125278855/227714502-f62c79b0-53c6-46d8-988a-a6841ae250d0.png)


### Further improvements other than a more advanced data association algorithm such as GNN or JPDA could be tuning the initial parameters chosen for measurement and process noise and as it was shown from my experiment the threshold considered for track score in track management. Additionally the state vector and motion model can also be extended to consider acceleration and orientation of the vehicle
