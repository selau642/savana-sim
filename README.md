# Mission
To ensure the survival of human race, we need to make Space Construction Vehicles(SCVs) harvest minerals faster

This program is to train SCVs to drive as fast as possible on the race track

May the fastest SCV wins! 

# Prerequisite
Make sure you have the following installed

ros2 galactic 
rmf_demos 
gazebo
rviz

# How to launch Space Construction Vehicles 
start wsl and run
```
source /opt/ros/galactic/setup.bash
ros2 launch scv.launch.xml
```
This will start SCVs on motorball.race map ...
SCV ready!

# Give SCVs Instructions to work
https://open-rmf.github.io/rmf-panel-js/

Send Loop tasks to make it move around

# Make Your Own World
1. Change the map moondance.map.yaml
2. make Gazebo 3D world 
```
ros2 run rmf_building_map_tools building_map_generator gazebo <map_yaml_file> <gazebo_world_file_name> <gazebo_output_directory>
```

```
ros2 run rmf_building_map_tools building_map_generator gazebo moondance.map.yaml moondance.world . 
```
Note the . at the end which means gazebo_output_directory = .
which is the current folder for command-center

Output: 
./building_L1
.rmf_schedule_node.yaml
moondance.world

3. make RViz nav_graph file called 0.yaml
```
ros2 run rmf_building_map_tools building_map_generator nav <map_yaml_file> <output_nav_graphs_dir>
```

```
ros2 run rmf_building_map_tools building_map_generator nav moondance.map.yaml .
```

4. update files
scv.launch.xml 
rmf.launch.xml
to use moondance.map.yaml, moondance.world 

5. Launch
```
source /opt/ros/galactic/setup.bash
ros2 launch scv.launch.xml
```

SCV Ready!

# Download models
you can download old models here
```
ros2 run rmf_building_map_tools building_map_model_downloader \
  ${building_map_path} -f -e ~/.gazebo/models
```
or manually download new models on the ignition website
