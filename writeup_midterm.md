# Sensor Fusion - Midterm: 3D object detection

#### In this project four steps of 3D object detection including 
#### 1.visualization and analysis of input data, here Lidar measurements from waymo dataset
#### 2.preprocessing of data in order to be used in related deep learnig algorithms
#### 3.performing object detection using a pretrained model here resnet and visualization of result
#### 4.Evaluation of result and computation of detection metrics i.e. precision and recall

### 1. in this step range and intensity images are stacked, visualized and cropped to present the car forward view. this result the following:

![range_image_screenshot_24 03 2023](https://user-images.githubusercontent.com/125278855/227633621-1021a5d9-ca1f-498e-8a05-c66d4828a2cd.png)
### In addition the point cloud is visualized for 200 frames. here different views of vehicles are identified 
![step1](https://user-images.githubusercontent.com/125278855/227635244-41ce0f24-9aa1-4ca4-b492-e0daa1ada48b.png)
![step1_2](https://user-images.githubusercontent.com/125278855/227635266-da7b4487-205d-4d1a-9b53-e56b4046007a.png)
![step1_3](https://user-images.githubusercontent.com/125278855/227635293-a67dbb2a-fad5-4c2a-9c99-618709945fe6.png)
![step1_4](https://user-images.githubusercontent.com/125278855/227635313-301c3864-b49d-4b8c-8989-dff108d4d422.png)
![step1_5](https://user-images.githubusercontent.com/125278855/227635339-1a729479-fa5f-4c84-b7c9-a0ea1d7e3c72.png)

### 2. In this step the x,y coordinate from the Lidar point cloud are converted to the x,y pixels in bird eye view and vidualized  
![step2_pcl_vis](https://user-images.githubusercontent.com/125278855/227639704-d704161b-346e-456f-8b18-9439c114c61c.png)

### additionally intensity and height values are each visualized on bird eye view and respectively resulted the following:
![img_intensity_screenshot_23 03 2023](https://user-images.githubusercontent.com/125278855/227639753-cbfd2f90-8ca5-467b-8f0b-9a44b549cb66.png)
![img_height_screenshot_23 03 2023](https://user-images.githubusercontent.com/125278855/227639770-7b8ce520-a36c-4cee-bc3f-eb054cac4527.png)

### 3. In this step resnet pretrained modelused to detect the vehicles in bird eye view image to visualize the detection the output are converted in bounding boxed format
![labels vs  detected objects_screenshot_24 03 2023](https://user-images.githubusercontent.com/125278855/227642160-ed4480c1-b141-44e5-b348-16688656ff01.png)


### 4. Finally the evaluation of detection is done based on iou values between boxed of label and detected objects and using a threshold the true positives are counted. accordingly the precision and recall values are calculated for 100 frames:  precision = 0.9539473684210527, recall = 0.9477124183006536

![evaluationResult](https://user-images.githubusercontent.com/125278855/227642705-ddd9bbee-bdaf-43b3-8907-0e4a5c542dda.png)

