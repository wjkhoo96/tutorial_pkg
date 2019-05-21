# Run
1. [REMOTE] 
    ```
    roscore
    ```
2. [TURTLEBOT3] 
    ```
    roslaunch turtlebot3_bringup turtlebot3_robot.launch
    ```
3. [TURTLEBOT3] 
    ```
    roslaunch turtlebot3_bringup turtlebot3_rpicamera.launch
    ```
4. [REMOTE]
    Compile .cpp by building with catkin_make
    ```
    cd ~/catkin_ws/
    catkin_make
    ```
5. [REMOTE]
    
    Run both navigation and follower functions.
    ```
    roslaunch tutorial_pkg follower_navigation.launch
    ```

# Guide
## Setup
1. Follow steps
    ```
    http://emanual.robotis.com/docs/en/platform/turtlebot3/appendix_raspi_cam/
    ```
2. Run
    ```
    git clone https://github.com/ros-teleop/teleop_twist_keyboard.git
    ```
## Steps
### Follower
1. [REMOTE] 
    ```
    roscore
    ```
2. [TURTLEBOT3] 
    ```
    roslaunch turtlebot3_bringup turtlebot3_robot.launch
    ```
3. [TURTLEBOT3] 
    ```
    roslaunch turtlebot3_bringup turtlebot3_rpicamera.launch
    ```
4. [REMOTE] 
    ```
    rosrun image_transport republish compressed in:=raspicam_node/image raw out:=/raspicam_node/image
    ```
    for testing 
    ```
    rqt_image_view
    ```
5. [REMOTE] 
    ```
    rosrun find_object_2d find_object_2d image:=raspicam_node/image
    ```
6. Pick an image(/image_rec/9.png)to recognise and save it. To test it try
    ```
    rostopic echo /objects
    ```
7. Compile .cpp by building with catkin_make
    ```
    cd ~/catkin_ws/
    catkin_make
    ```
    remember to compile the code everytime you change the code.

8. [REMOTE] 
    ```
    roslaunch tutorial_pkg tutorial_pkg.launch
    ```
9. The turtlebot should move foward once it sees the object.
### Navigation
1.  [REMOTE]
    Run RViz
    ```
    roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/maps/map2.yaml
    ```
2.  [REMOTE]
    Run goal.py
    ```
    rosrun tutorial_pkg goal.py
    ```