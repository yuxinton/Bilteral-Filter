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

Open third window to extract the bag files and feed into ORB_SLAM2
rosparam set use_sim_time true 
rosbag play sequence03.bag --clock -r 0.5 
After playing the bag file, exit ORB_SLAM2 and save the trajectory 

Install the evaluation software 
sudo apt install python-pip 
pip install evo --upgrade --no-binary evo 
after installing the evaluation software 
evaluate the absolute pose error by 
evo_ape tum truth.txt before_filter.txt -p -va
evo_ape tum truth.txt after_filter.txt -p -va 
Generate the comparison for trajectory by 
evo_traj tum --ref=truth.txt before_filter.txt after_filter.txt -p -va 

