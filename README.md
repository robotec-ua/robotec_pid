# PID Controller by Robotec
PID controller - it's the most powerful and famous type of controllers. It has the ability to correct given data using previous errors (inconsistency between desired and measured values).

## Libraries
* The heart of the package is [simple-ros-pid](https://github.com/m-lundberg/simple-pid) package.

## ROS Interfaces
This part describes various ROS-related interfaces such as parameters and topics.

### Parameters

* `~p: float`

    Proportional coefficient of the controller
    Default: `1.0`

* `~i: float`

    Integral coefficient of the controller
    Default: `0.1`

* `~d: float`

    Derivative coefficient of the controller
    Default: `0.05`

* `~publish_rate: int`

    The rate of the main loop of the node.
    Default: `100`

* `~input: string`

    Input data topic (data to adjust using the PID controller)

* `~setpoint: string`

    Setpoint topic (the desirable value)

* `~adjusted: string`

    Data after the correction

### Topics Published

* `~adjusted: Float64`

    Result of PID correction


### Topics Subscribed

* `~input: sensor_msgs/Image`

    Input image to be proccessed


## Project structure
```
.
├── cfg
│   └── pid.cfg
├── launch
│   └── pid.launch
├── scripts
│   └── pid.py
├── CMakeLists.txt
├── LICENSE
├── package.xml
├── README.md
└── setup.py

```

### Folders
*  `./launch`  - *.yaml roslaunch files
*  `./scripts`  - main folder of the project (contains executables)
*  `./cfg`  - configuration files for the `dynamic_reconfigure` package

### Files
The project uses following files

#### Launch
*  `pid.launch`  - starting the node (example of use)

#### Package
*  `pid.py` - the main node (corrects errors of the received data)

#### ROS
*  `pid.cfg` - a configuration file for the `dynamic_reconfigure` package

## Example of use
To start the controller you should change the parameters in `launch/pid.launch` and then run :
~~~bash
$ roslaunch robotec_pid pid.launch
~~~
