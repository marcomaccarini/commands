# Sealant Deposition Use Case



# 1.Deposition (robot connected to the router)
```console
cd assassin_ws
mkdir src/robot_control/include
catkin build
source devel/setup.bash
```
## 1.1. Terminal A
```console
roslaunch ur_robot_driver ur10e_bringup.launch robot_ip:=192.168.1.30
```

Replace ‘robot_ip’ with the robot’s IP

## 1.2. Terminal B
### For a simulated Robot in gazebo (Default)
```console
roslaunch ur10e_moveit_config ur10e_moveit_planning_execution.launch
```
### For a real Robot (once the driver is up and running)
```console
roslaunch ur10e_moveit_config ur10e_moveit_planning_execution.launch sim:=false
```

## 1.3. Terminal C
```console
rosrun robot_control deposition_action_server
```



# 2. Quality inspection 

## 2.1 Terminal D
```console
rosrun robot_control quality_inspection_action_server
```
## 2.2 Publish a message to the topic
```console
rostopic pub /quality_inspection_AS/goal robot_control/QualityInspectionActionGoal ”header:
  seq:0
  stamp:: 0
	secs: 00
	nsecs: 0 ‘’
  frame_id: ‘’
goal_id:
  stamp::0
	secs:00
	nsecs:0
  id:’’
goal: 0.0
  x1: 0.0
  y1: 0.0”
  y2:0.0
  y2:0.0”
```


# 3. Rework
## 3.1 Terminal E
```console
rosrun robot_control sealant_rework_action_server
```


