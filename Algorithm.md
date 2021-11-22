# Algorithm Setup and run

## Setup Evironment
Install Keras and Tensorflow 1.x with python 3.6 only. Anything higher will need Tensorflow 2 which is slow.

## Run Simple DQN 
Run the unity build and ```roslaunch ros_tcp_endpoint endpoint.launch``` to start ROS communication.
1. ```conda activate dqn```
2. ```rosrun sim2real DQN_official.py```
