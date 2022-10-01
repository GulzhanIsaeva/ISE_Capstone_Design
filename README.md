# 1.1 ROS Noetic Installation

## 1.2 Setup your sources.list

Setup your computer to accept software from packages.ros.org.

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```

![image](https://user-images.githubusercontent.com/90166739/193383972-9dff6b22-3190-4849-8834-ec3ae2ba046c.png)

## 1.3 Set up your keys

```
sudo apt install curl # if you haven't already installed curl
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
![image](https://user-images.githubusercontent.com/90166739/193384108-c584053a-1c2b-4c9f-b812-025ced3b3ead.png)


## 1.4 Installation

Make sure your Debian package is up-to-date:

```
sudo apt update
```

Desktop-Full Install: 

```
sudo apt install ros-noetic-desktop-full
```

## 1.5 Environment setup

You must source this script in every bash terminal you use ROS in.

```
source /opt/ros/noetic/setup.bash
```

bash

```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

zsh

```
echo "source /opt/ros/noetic/setup.zsh" >> ~/.zshrc
source ~/.zshrc
```


## 1.6 Dependencies for building packages

To install this tool and other dependencies for building ROS packages, run:

```
sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential
```

###### 1.6.1 Initialize rosdep

rosdep enables you to easily install system dependencies for source you want to compile and is required to run some core components in ROS

```
sudo apt install python3-rosdep
```

With the following, you can initialize rosdep.

```
sudo rosdep init
rosdep update
```
