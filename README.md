# Sim2Real
Converting noisy LIDAR into smoother LIDAR data , to look alike a simulated model.

## Run TurtleBot in ROC laptop
| :zap:        Use phone's hotspot, from laptop connect to Hardy wifi. Notedown IP from phone or run 'ifconfig' from terminal|
|-----------------------------------------|

### Training
1. Conda environment  
```vim
source activate dqn
```
2. Run stage 4 gazebo command  
```vim
roslaunch turtlebot3_gazebo turtlebot3_stage_4.launch
```
3. Run the custom made python program  
```vim 
rosrun dqn_turtlebot DQN_official.py
```
4. Check Rviz 
```vim
roslaunch turtlebot3_gazebo turtlebot3_gazebo_rviz.launch
```

### Prediction/Testing
1. Conda environment 
```vim
source activate dqn
```
2. Create custom environment with empty gazebo world 
```vim
roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch
```
3. Run the prediction python program, insert the episode number in python program to load the specific model.
```vim
rosrun dqn_turtlebot DQN_predict.py
```
4. Check Rviz for gazebo using step 4 of training.

### Predicting using real TurtleBot
#### Connecting TurtleBot and laptop
| :zap:        Use phone's hotspot, switch ON TurtleBot (autoconnects to Hardy wifi) and connect from laptop to same. Notedown IP of both from phone|
|-----------------------------------------|

To change IP in laptop, In terminal type
```vim
nano ~/.bashrc
```
Goto to end of file Alt+/
```vim
export ROS_MASTER_URI=http://{IP_ADDRESS_OF_Laptop}:11311
export ROS_HOSTNAME={IP_ADDRESS_OF_Laptop}
```
Ctrl+s & Ctrl+x, To finalize the changes
```vim
source ~/.bashrc
```
To change IP in TurtleBot, first connect to TurtleBot via SSH.
```vim
ssh ubuntu@{IP_ADDRESS_OF_TurtlebBot}
password: turtlebot
```
In terminal
```vim
nano ~/.bashrc
```
Goto to end of file Alt+/
```vim
export ROS_MASTER_URI=http://{IP_ADDRESS_OF_Laptop}:11311
export ROS_HOSTNAME={IP_ADDRESS_OF_TurtlebBot}
```
Ctrl+s & Ctrl+x, To finalize the changes
```vim
source ~/.bashrc
```
#### Running TurtleBot
1. In Terminal run 
```vim
roscore
```
2. In new terminal, connect to TurtleBot
```vim
ssh ubuntu@{IP_ADDRESS_OF_TurtlebBot}
password: turtlebot
```
3. Initiate all the TurtelBot sensors and motors
```vim
roslaunch turtlebot3_bringup turtlebot3_robot.launch
```
4. In new terminal, open Rviz to look at Lidar data
```vim 
roslaunch turtlebot3_bringup turtlebot3_model.launch
```
or
```vim
roslaunch turtlebot3_slam turtlebot3_slam.launch
```
for viewing as a map.
5. In new terminal, start the predict program
```vim
rosrun dqn_turtlebot DQN_predict.py
```
6. To view the reward graph, in new terminal
```vim
rosrun dqn_turtlebot result_graph
```
