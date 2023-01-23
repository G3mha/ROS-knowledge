# ROS Cheat Sheet

## Quick Reference

1. Workflow: URDF, joint axis test, plugins addition (sensors in Rviz), simulations set (create physical elements Gazebo)

2. ROS Resource and Tutorials: [ROS Wiki](http://wiki.ros.org/ROS/Tutorials)

3. Check what version of ROS you are using: `rosversion -d`

4. If you change the ROS version (between 1 and 2) in the bashrc file, you need to run `source ~/.bashrc` to update the changes.

5. Suggested VSCode Extensions:
    - ROS
    - ROS Snippets
    - Python
    - XML
    - XML Tools

## Rviz

Rviz is a 3D visualization tool for ROS. It is used to visualize the robot model, the robot state, and sensor data. Basically, it is limited to the robot's knowledge.

## Gazebo

Gazebo is a 3D dynamic simulator with the ability to accurately and efficiently simulate populations of robots in complex indoor and outdoor environments. It is used to simulate the robot's behavior in the real world.

## File Structure

-  Workspace: a directory containing all the ROS packages that you are currently working on. *You can have multiple workspaces on the same computer*.

- Package: a directory containing all the files related to a specific task. There a several types of packages available for download (developed by the open-source community): executable, libraries, messages, services, etc. *You can share packages between workspaces*.

### Create a workspace

Open up the terminal and type the following command:

```bash
ls -a
code .bashrc
```

Paste the following lines at the end of the file:

```bash
source /opt/ros/noetic/setup.bash
```

Go back to the terminal and type the following command:

```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```

### Create a package

Go to the source folder of your workspace and type the following command (replace `<package_name>` with the name of your package and `[depend1] [depend2] [depend3]` with the dependencies of your package):

```bash
cd ~/catkin_ws/src
catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
```

## Making a robot

### URDF

Universal Robot Description Format (URDF) is an XML file format used in ROS to describe all elements of a robot. It is used by robot_state_publisher to publish the state of the robot to tf, and by the robot_model and robot_state to represent the robot.

### Customizing robot design in URDF

Questions to ask yourself:

1. What is the robot type? (e.g. mobile, manipulator, etc.)

2. What are the joint types? (e.g. revolute, prismatic, continuous, fixed, etc.) - *Joints are not apperent since they are imaginary*.

3. What are the link lenghts (parts that compose the robot)? (geometrical, physical and color properties) - *Links are apperent since they are physical*.

4. What is the total footprint of the robot? (e.g. box size, cylinder size, mesh size, etc.)