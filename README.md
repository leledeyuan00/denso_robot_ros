Please refer to https://wiki.ros.org/denso_robot_ros.


## General details about robot description packages

This description package follows, as much as possible, the recommendations from [ROS-Industrial Consortium about robot support packages](https://wiki.ros.org/Industrial/Tutorials/WorkingWithRosIndustrialRobotSupportPackages).
The general package structure is the following:

```
<manufacturer|robot_name>_description/             # Robot's description files
├── [CMakeLists.txt]                               # if ament_cmake is used (recommended)
├── package.xml
├── [setup.py]                                     # if amend_python is used
├── [setup.cfg]                                    # if amend_python is used
├── config/                                        # general YAML files for a robot
│   └── <robot_name>_<someting_specific>.yaml
├── launch/                                        # launch files related to testing robots' description
│   └── test_<robot_name>_description.launch.py
├── meshes/                                        # meshes used in <robot_name>_macro.urdf.xacro
│   ├── collision
│   │   └── <robot_name|robot_model>               # meshes are sorted by robot name or model
│   │       ├── <link_xy>.stl
│   │       └── ...
│   └── visual
│       └── <robot_name|robot_model>
│           ├── <link_xy>.dae
│           └── ...
├── rviz/                                          # rviz display configurations
│   └── <robot_name>_default.rviz
└── urdf/                                          # URDF file for the robot
    ├── common.xacro                               # Common XACRO definitions
    ├── <robot_name>.urdf.xacro                    # Main URDF for a robot - loads macro and other files
    └── <robot_name|robot_model>
        ├── <robot_name>_macro.xacro               # Macro file of the robot - can add prefix, define origin, etc.
        └── <robot_name>_macro.ros2_control.xacro  # URDF-part used to configure ros2_control

```

### Testing the validity of robot description

1. Go to the root of your workspace folder (there where `src`, `build`, `install` and `log` files are).
2. Install the package by calling `colcon build --symlink-install --packages-select denso_robot_description`
3. (Re-)Source environment `source install/setup.bash`
4. Launch description test:
   ```
   ros2 launch denso_robot_description test_denso_robot_description.launch.py
   ```

If there are no issues with the description, two windows are opened: `rviz2` and `Joint State Publisher`.
Rviz2 visualizes the robot's state and Joint state Publisher to changes joint values using sliders or generates random but valid configurations.


## General details about robot description packages

This description package follows, as much as possible, the recommendations from [ROS-Industrial Consortium about robot support packages](https://wiki.ros.org/Industrial/Tutorials/WorkingWithRosIndustrialRobotSupportPackages).
The general package structure is the following:

```
<manufacturer|robot_name>_description/             # Robot's description files
├── [CMakeLists.txt]                               # if ament_cmake is used (recommended)
├── package.xml
├── [setup.py]                                     # if amend_python is used
├── [setup.cfg]                                    # if amend_python is used
├── config/                                        # general YAML files for a robot
│   └── <robot_name>_<someting_specific>.yaml
├── launch/                                        # launch files related to testing robots' description
│   └── test_<robot_name>_description.launch.py
├── meshes/                                        # meshes used in <robot_name>_macro.urdf.xacro
│   ├── collision
│   │   └── <robot_name|robot_model>               # meshes are sorted by robot name or model
│   │       ├── <link_xy>.stl
│   │       └── ...
│   └── visual
│       └── <robot_name|robot_model>
│           ├── <link_xy>.dae
│           └── ...
├── rviz/                                          # rviz display configurations
│   └── <robot_name>_default.rviz
└── urdf/                                          # URDF file for the robot
    ├── common.xacro                               # Common XACRO definitions
    ├── <robot_name>.urdf.xacro                    # Main URDF for a robot - loads macro and other files
    └── <robot_name|robot_model>
        ├── <robot_name>_macro.xacro               # Macro file of the robot - can add prefix, define origin, etc.
        └── <robot_name>_macro.ros2_control.xacro  # URDF-part used to configure ros2_control

```

### Testing the validity of robot description

1. Go to the root of your workspace folder (there where `src`, `build`, `install` and `log` files are).
2. Install the package by calling `colcon build --symlink-install --packages-select denso_robot_description`
3. (Re-)Source environment `source install/setup.bash`
4. Launch description test:
   ```
   ros2 launch denso_robot_description test_denso_robot_description.launch.py
   ```

If there are no issues with the description, two windows are opened: `rviz2` and `Joint State Publisher`.
Rviz2 visualizes the robot's state and Joint state Publisher to changes joint values using sliders or generates random but valid configurations.
