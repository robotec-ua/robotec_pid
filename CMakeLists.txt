cmake_minimum_required(VERSION 2.8.3)
project(robotec_pid)

generate_dynamic_reconfigure_options(
    cfg/pid.cfg
)

#
find_package(catkin REQUIRED COMPONENTS std_msgs sensor_msgs message_generation)

#
catkin_python_setup()

#
catkin_package(
    CATKIN_DEPENDS message_runtime dynamic_reconfigure
    )
add_dependencies(example_node ${PROJECT_NAME}_gencfg)
