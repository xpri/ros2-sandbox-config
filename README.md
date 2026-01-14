# ros2-sandbox-config

Holds the manifest of all packages used in my testbed for ROS 2. If anyone wants to copy my testbed and packages, then this is where the honey is.

**MAKE SURE TO HAVE ROS2 JAZZY INSTALLED BEFOREHAND. Please use Linux!**

### Anyhow, enjoy :)!

## 🚀 Getting Started

To replicate this testbed on your local machine, follow these steps:

### 1. Create a Workspace

Open your terminal and create a new ROS 2 workspace:

`mkdir -p ~/ros2_sandbox_ws/src`

`cd ~/ros2_sandbox_ws`


### 2. Clone this Configuration Repository

Clone this specific configuration repository directly into your workspace root:

`git clone [https://github.com/xpri/ros2-sandbox-config.git](https://github.com/xpri/ros2-sandbox-config.git) .`

(make sure to include the period at the end)


### 3. Import Package Dependencies

Use the vcs tool to automatically clone all the required C++ and Python packages listed in the .repos file into your src folder:

**Install vcstool if you don't have it:**

`sudo apt update && sudo apt install python3-vcstool -y`

`vcs import src < project_config.repos`


### 4. Build the Workspace

Install any missing system dependencies and build the project using colcon:

## Update rosdep to find the latest package definitions
`rosdep update`

`rosdep install --from-paths src --ignore-src -y`

## Build the workspace and don't forget to source Jazzy!
`source /opt/ros/jazzy/setup.bash`

`colcon build`

`source install/setup.bash`


#### 5. Run the Project

Once the build is finished, you can run the nodes in separate terminals (remember to source in each):

Terminal 1 (Talker):

`source install/setup.bash`

`ros2 run cpp_talker_package cpp_talker_package`


Terminal 2 (Listener):

`source install/setup.bash`

`ros2 run cpp_listener_package cpp_listener_package`


This setup ensures that you don't have to manually git clone every single package one by one. One command pulls my whole ROS2 project together!
