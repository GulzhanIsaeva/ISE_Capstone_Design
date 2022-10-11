# Build a Simulated Mobile Robot Base Using ROS

![image](https://user-images.githubusercontent.com/90166739/193480976-a7a760ba-5f8c-4b59-a129-f5472eef70f4.png)

In this 1st ROS read.me file, we will build a mobile robot base from scratch using ROS. In the 2nd ROS file, we will add a robotic arm to this base.

## 1. Install ROS Packages

```
sudo apt-get install ros-noetic-ros-control
sudo apt-get install ros-noetic-ros-controllers
sudo apt-get install ros-noetic-gazebo-ros-control
```

## 2. Create a ROS Package

In a new terminal window, move to the src (source) folder of your workspace.

```
cd ~/catkin_ws/src
```
Now create the package.

```
catkin_create_pkg mobile_manipulator_body std_msgs roscpp rospy
cd ~/catkin_ws/
catkin_make --only-pkg-with-deps mobile_manipulator_body
```

## 3. Create Folders

Open a new terminal window and move to your package.

```
roscd mobile_manipulator_body
```

Create these four folders:

```
mkdir config launch meshes urdf
```

## 4. Build the Base of the Robot

Now move to your meshes folder.

```
cd meshes
```

Download all the mesh files through this link:
https://drive.google.com/drive/folders/1-NTb0bWy1NfOFHB96pBzhM4gDQA02zE-?usp=sharing

Put the mesh files into your meshes folder inside your mobile_manipulator_body package.


Check to see all the files are in there. **(insert screenshot below the code)**

```
dir
```

Move to the urdf folder.

```
cd ..
cd urdf
```

We created a file named robot_base.urdf. 
In this file, we will define the four wheels of the robot and the base.

```
gedit robot_base.urdf
```

Copy this code for robot_base.urdf into that file: https://drive.google.com/drive/folders/1oX9Eyd1fKWX1HOQfMhK5aJoHKeJjznzM?usp=sharing
Save and close the file.



Now, let’s launch RViz to see what our robot looks like so far. **(insert screenshot below the code)**

```
roscd mobile_manipulator_body/urdf/
roslaunch urdf_tutorial display.launch model:=robot_base.urdf
```


Move the wheels using the sliders and set up the configuration parameters for the controllers.
**(insert screenshot)**


Open a new terminal window.
Go to the config file of your package.

```
roscd mobile_manipulator_body/config/
```


Now create a file named control.yaml.

```
gedit control.yaml
```

Add the control.yaml code inside there: https://drive.google.com/drive/folders/1UlkrsKflhNXCpGrL4QA26yL3ezgKfteg?usp=sharing
Save and close the file.


## 5. Launch the Base of the Robot

Now let’s launch the base of the robot.
Open a new terminal window, and go to the package.

```
roscd mobile_manipulator_body/launch/
```


Create a new launch file.

```
gedit base_gazebo_control.launch
```

Save and close the file and then launch the robot in Gazebo.



Open a new terminal window and move to your catkin workspace.

```
cd ~/catkin_ws/
roslaunch mobile_manipulator_body base_gazebo_control.launch
```


Here is how the robot looks:
![image](https://user-images.githubusercontent.com/90166739/193480976-a7a760ba-5f8c-4b59-a129-f5472eef70f4.png)



Here are the active ROS topics.
```
rostopic list
```


You can steer the robot by opening a new window and typing:

```
rosrun rqt_robot_steering rqt_robot_steering
```



You will need to change the topic inside the GUI to:

```
/robot_base_velocity_controller/cmd_vel
```

![gui](https://user-images.githubusercontent.com/90167023/193490778-a1cf56fa-299c-4f97-bd9c-196fdecf1cb0.jpg)

<br />

To see the velocity messages, open a new window and type:

```
rostopic echo 
/robot_base_velocity_controller/cmd_vel
```

![speed](https://user-images.githubusercontent.com/90167023/193491393-b7eb4da1-dc83-417b-8aad-98d51c664198.jpg)
