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
6. Pick an object to recognise and save it. To test it try
    ```
    rostopic echo /objects
    ```
7. Edit the id of object in _action_controller.cpp_ , example the object id is 1
    ```
    #define ARROW_UP 1
    int id = 1
    ```
    and compile the code using
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