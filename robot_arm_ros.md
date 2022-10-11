# Build a Simulated Robot Arm Using ROS


## Build the Robot Arm

Open a new terminal window.

Move to the urdf folder of your package.

```
roscd mobile_manipulator_body/urdf/
```

Now create a file named robot_arm.urdf.

```
gedit robot_arm.urdf
```

Add the robot_arm.urdf code inside there.
Save and close the file.



## Test the Robot Arm

Launch the robot arm, open a new terminal window, and go to the package.

```
roscd mobile_manipulator_body/urdf/
roslaunch urdf_tutorial display.launch model:=robot_arm.urdf
```


Open a new terminal window and go to the config file of your package.

```
roscd mobile_manipulator_body/config/
```

Now create a file named arm_control.yaml.

```
gedit arm_control.yaml
```

Add the arm_control.yaml code: https://drive.google.com/drive/folders/1UlkrsKflhNXCpGrL4QA26yL3ezgKfteg?usp=sharing

Save and close the file.


Now create a file named joint_state_controller.yaml.

```
gedit joint_state_controller.yaml
```

Add the joint_state_controller.yaml code: https://drive.google.com/drive/folders/1UlkrsKflhNXCpGrL4QA26yL3ezgKfteg?usp=sharing

Save and close the file.

## Launch the Robot Arm

Open a new terminal window, and go to the package.

```
roscd mobile_manipulator_body/launch/
```

Create a new launch file.

```
gedit arm_gazebo_control.launch
```

Add the arm_gazebo_control.launch code: https://drive.google.com/drive/folders/1Acv58Up41u5pYDM5yE1jru_YoVbn_rCl?usp=sharing

###### Launch the robot in Gazebo.

Open a new terminal window and move to your catkin workspace.

```
cd ~/catkin_ws/
roslaunch mobile_manipulator_body arm_gazebo_control.launch
```

Here is how the robot arm looks.
![arm](https://user-images.githubusercontent.com/90167023/193492494-a6944356-5af2-43b6-87d8-c5b6cfff0614.jpg)
 
Here are the active ROS topics:

```
rostopic list
```
![rostopic](https://user-images.githubusercontent.com/90167023/193492704-3bf55a5b-258a-48e3-a3c6-bfa636b1c589.jpg)

<br />


Open a new terminal, and type this command to move the robot arm a little bit:

```
rostopic pub /arm_controller/command trajectory_msgs/JointTrajectory '{joint_names: ["arm_base_joint","shoulder_joint", "bottom_wrist_joint", "elbow_joint","top_wrist_joint"], points: [{positions: [-0.1, 0.5, 0.02, 0, 0], time_from_start: [1,0]}]}' -1
```
![move arm](https://user-images.githubusercontent.com/90167023/193493065-7a1442d6-4b0c-4ee0-a336-2bdb8dc55f8c.jpg)

<br />

Type this command to bring the robot back to the home position.

```
rostopic pub /arm_controller/command trajectory_msgs/JointTrajectory '{joint_names: ["arm_base_joint","shoulder_joint", "bottom_wrist_joint", "elbow_joint","top_wrist_joint"], points: [{positions: [0, 0, 0, 0, 0], time_from_start: [1,0]}]}' -1
```



https://user-images.githubusercontent.com/90167023/193494826-5f47a718-3f90-483b-9b84-5a1adc01e5af.mp4

