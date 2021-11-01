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

## Publish new message (LIDAR) from Unity
In the Github of ros_unity_integration, by default for publishing and subscribing only two types of messages are provided, Color and PosRot.
To create a new type of messages for example like LIDAR. the follwoing has to be done.
1. Goto home/catkin_ws/src/unity_robotics_demo_msgs/msg and make a copy of  PosRot.msg and rename as Lidar.msg.
2. Open Lidar.msg and type ```float32[] range```, inorder to create a float array under the heading ```range```.
3. Need to genereate Laser.msg into unity's C# message and ROS's python message.
4. Open Unity and Robotics->Generate ROS messages and Rebuild message.
![image](https://user-images.githubusercontent.com/63108972/139685614-ca874c51-5c4b-4499-8af5-eb6b82dbea2e.png)
This generates C# laser message in asset folder.
5. For python message, open terminal, goto catkin_ws and type catkin_make. this generates the message file in cartkin/ws/devel/lib/python3/dist-packages/unity-robotic-demo-msgs/msg/_Laser.py
6. Now create simple publisher script in Unity and call the messages like below
```ros = ROSConnection.GetOrCreateInstance();
ros.RegisterPublisher<LaserMsg>('lidar_msg');
LaserMsg scan = new LaserMsg{
    range = LidarScan,
        };
ros.Publish(LidartopicName, scan);```
