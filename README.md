# Dolly the robot

_It's a sheep, it's a dolly, it's a following robot. Clone Dolly now!_

Packages for launching Dolly demo, which uses Gazebo and ROS 2.

![Dolly city](dolly.gif)

Dolly has been tested on:

* ROS Crystal and upcoming ROS Dashing (as of 2019-04-03)
* Ubuntu Bionic and OSX Sierra

## Install

Install instructions for ROS Crystal + Ubuntu Bionic.

1. Install ROS Crystal as instructed [here](https://index.ros.org/doc/ros2/Installation/Linux-Install-Debians/).

1. Install `gazebo_ros_pkgs`, which also installs Gazebo:

        sudo apt install ros-crystal-gazebo-ros-pkgs

1. Clone Dolly:

        mkdir -p ~/ws/src
        cd ~/ws/src
        git clone https://github.com/chapulina/dolly

1. Build and install:

        cd ~/ws
        colcon build

## Run

1. Setup environment variables (the order is important):

        . /usr/share/gazebo/setup.sh
        . ~/ws/install/setup.bash
        export GAZEBO_RESOURCE_PATH=/home/`whoami`/ws/src/dolly/dolly_gazebo/worlds:${GAZEBO_RESOURCE_PATH}
        export GAZEBO_MODEL_PATH=/home/`whoami`/ws/src/dolly/dolly_gazebo/models:${GAZEBO_MODEL_PATH}

1. Launch Dolly in a city (this will take some time to download models):

        ros2 launch dolly_gazebo dolly.launch.py world:=dolly_city.world

1. Launch Dolly in an empty world:

        ros2 launch dolly_gazebo dolly.launch.py world:=dolly_empty.world

## Packages

This repository contains 2 packages:

* `dolly_follow`: Provides node with follow logic.
* `dolly_gazebo`: Robot model, simulation world and launch scripts.

# TODO

* Set Gazebo paths from launch file
* Make Dolly's model available to RViz

