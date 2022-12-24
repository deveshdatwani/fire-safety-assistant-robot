****************** Requirements ******************

* ROS 1 Noetic
* Python 3
* Turtlebot3 packages
* Scipy (version=1.1.0) Library
* Matplotlib
* Numpy
* PIL
* OpenCV
* Scikit learn
  
****************** Running the code ******************

1. Run "explore.launch": 
	Args: map_type:=(no_obs, obs1, obs2, obs3)   
	Descr: Launches the Gazebo sim with the specific world (args: map_type) and the turtlebot3 along with SLAM Gmapping package and Rviz

2. Run "explore.py":
	Descr: Python script to publish goal points, for turtlebot3 to navigate and map the environment 
	Output: Saves the binary map to /saved_maps folder with file name current_map.png

3. Run "detect_changes.py": (Needs scipy version scipy 1.1.0)
	Descr: Python script to detect obstacles
	Output: Saves the change map to /saved_maps/change_map folder with file name change_map.png 
	
   Note: If the scipy version issue exists, create the virtual environment with python. Install the requirements using requirements.txt file attached. Go to the catkin_ws and 		 use the command "source/venv/bin/activate". Then go to the script directory and run the file as python3 filename.py

4. Run "score.py":
	Descr: Python script to find the risk score for each room
	Output: Prints out the Path length score and Gradient score for each room

****************** Other Scripts and Launch files ******************

1. RRT.py: RRT Class containing algorithms for RRT, RRT* and Informed RRT*

2. grad_map.py: For visualizing gradients on the map

3. goal_sequence.py: For navigating turtlebot3 along a sequence of goal points using known map file(.yaml file) and AMCL

4. navigation.launch: For launching the world with turtlebot3 spawned, map_file in map server, run gmapping package and execute goal_sequence.py

5. robot_drive.launch: Drive turtlebot3 using teleop    

 

