# Implementation of Bilteral-Filter on Rosario Dataset
## Run ROS bagfiles of Rosario Dataset through ORB_SLAM2 
After install ORB_SALM2 and ROS, call roscore
```
roscore
```
Replace the ORBextractor.cc from the orignial ORB_SLAM2 with the ORBextractor.cc in this repo.

Recompile ORB_SLAM2 and add the directory to the 'ros_package_path', and then build the project.
```
export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:/home/yuxinton/ORB_SLAM2/Examples/ROS
./build.sh
./build_ros.sh
```
Download the orbslam_ros.yaml file from the web and put it in ORB_SALM2，synchronize ROS clock with the simulator and run the ORB_SLAM2 stereo camera node with the specified vocabulary and configuration files.
```
rosparam set use_sim_time true 
rosrun ORB_SLAM2 Stereo Vocabulary/ORBvoc.txt Examples/ROS/ORB_SLAM2/orbslam_ros.yaml.txt true 
```
Extract the sequence bag files and feed into ORB_SLAM2 with 0.5 speed.
```
rosparam set use_sim_time true 
rosbag play sequence03.bag --clock -r 0.5 
```
After playing the bag file, exit ORB_SLAM2 and save the trajectory.
## Install evaluation software 
Install the evaluation software [evo](https://github.com/MichaelGrupp/evo)
```
sudo apt install python-pip 
pip install evo --upgrade --no-binary evo 
```
After installing the evaluation software, evaluate the absolute pose error.
```
evo_ape tum truth.txt before_filter.txt -p -va
evo_ape tum truth.txt after_filter.txt -p -va 
```
Generate the comparison for trajectory by 
```
evo_traj tum --ref=truth.txt before_filter.txt after_filter.txt -p -va 
```

