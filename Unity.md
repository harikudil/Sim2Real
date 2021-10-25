# Unity - ROS
Unity can be programmed only using C#, Thanks to developers, ROS can be used for communicating between python and Unity.
![image](https://user-images.githubusercontent.com/63108972/138248159-ed95b3cc-683d-4327-b449-b83d7f7dd5b3.png)

## Ros in Unity
1. Follow the website to install URDF importer and ROS TCP connector
https://youtu.be/HV1v8mXNmLA
2. Complete the steps in https://github.com/Unity-Technologies/Unity-Robotics-Hub/blob/main/tutorials/ros_unity_integration/setup.md

## Run
1. In terminal,```roslaunch ros_tcp_endpoint endpoint.launch``` to launch  roscore and start the node.
2. In new terminal, run ```rosrun unity_robotics_demo pos_publisher.py``` to run the python code.

## ROS Unity integration
Follow the examples from 
https://github.com/Unity-Technologies/Unity-Robotics-Hub/blob/main/tutorials/ros_unity_integration/README.md
