# Implementation of Bilteral-Filter on Rosario Dataset
##
After install ORB_SALM2 and ROS, 

Open first window and call roscore 
rosecore 

Open second windown and re-compile ORB_SLAM2 
export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:/home/yuxinton/ORB_SLAM2/Examples/ROS
./build.sh
./build_ros.sh
download the orbslam_ros.yaml file from the web and put it
run ORB_SLAM2 software 
rosparam set use_sim_time true 
rosrun ORB_SLAM2 Stereo Vocabulary/ORBvoc.txt Examples/ROS/ORB_SLAM2/orbslam_ros.yaml.txt true 

Open third window and feed the bag files 
