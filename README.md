# Mimic_OpenManipulator
This project is for open manipulator hardware where the salve mimic the master trajectory using Python and the trajectory is saved in rosbag file to be later played

for the gravity compensation need to make the following lines

cd ~/catkin_ws/src/

git clone https://github.com/ROBOTIS-GIT/open_manipulator_controls.git

cd ~/catkin_ws && catkin_make


open dynamixel software (Dynamixel Wizard 2)

(For the master Robot only) (know the both USB port will use later)

make operation mode to be current control for all joints

(For both robots)

make the joints numbered from 11 -> 15

-to start the slave: (check the usb port id and use the right one)

roslaunch open_manipulator_hw open_manipulator_control.launch __ns:=slave baud_rate:=1000000 usb_port:=/dev/ttyACM0

-to start the launch file we made that will launch the master and make the gravity compensation for it and will start slave controls (check the USB port id and use the right one)

roslaunch master_slave_new master_slave_new.launch usb_port:=/dev/ttyACM1

-to start our Python code (which will make the mimic or record in rosbag)

rosrun master_slave_new final.py

-interact with the terminal for the mimic and trajectory record and play
