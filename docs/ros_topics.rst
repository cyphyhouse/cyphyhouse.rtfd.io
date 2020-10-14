.. _ros-topics:

Predefined ROS Topics
=====================

Shared between Simulation and Deployment
----------------------------------------

.. code-block:: yaml

    waypoint        geometry_msgs/PoseStamped
    waypoint_tobest geometry_msgs/PoseStamped  # Not used yet
    reached         std_msgs/String

Topic names are all lower cases by convention.
Note that the topics are not global names.
For deployment, we can specify environment variable ``ROS_NAMESPACE`` for each
device so that ``ros_launch`` will append a prefix to the topics.
That is the topic at runtime becomes ``/{ROS_NAMESPACE}/waypoint``.
``ROS_NAMESPACE`` should be set with an unique ROS name such as IP with port.

In the simulator, ``*.launch`` is auto-generated.
We explicitly generate a namespace for each simulated agent.
E.g., the topic ``waypoint`` becomes ``/{AGENTID}/waypoint`` in simulation
with the unique ``AGENTID`` as the namespace.

See `Remapping Arguments`_ for more detail.

.. _Remapping Arguments: http://wiki.ros.org/action/fullsearch/Remapping%20Arguments


Simulation only
---------------

Drone Specific
~~~~~~~~~~~~~~

.. code-block:: yaml

    /drone{id}/ground_truth/state nav_msgs/Odometry
    /drone{id}/cmd_vel            geometry_msgs/Twist
    /drone{id}/goals              std_msgs/Float32MultiArray


Car Specific
~~~~~~~~~~~~

.. code-block:: yaml

    /car{id}/racecar/left_rear_wheel_velocity_controller/command      std_msgs/Float64
    /car{id}/racecar/right_rear_wheel_velocity_controller/command     std_msgs/Float64
    /car{id}/racecar/left_front_wheel_velocity_controller/command     std_msgs/Float64
    /car{id}/racecar/right_front_wheel_velocity_controller/command    std_msgs/Float64
    /car{id}/racecar/left_steering_hinge_position_controller/command  std_msgs/Float64
    /car{id}/racecar/right_steering_hinge_position_controller/command std_msgs/Float64

    # goto.py
    /car{id}/ground_truth/state nav_msgs/Odometry
    /car{id}/goals              std_msgs/Float32MultiArray

    # ackermann_car.py
    /car{id}/ackermann_cmd      ackermann_msgs/AckermannDriveStamped


Deployment only
---------------

Vicon
~~~~~

.. code-block:: yaml

    /vrpn_client_node/{vicon_obj}/pose  geometry_msgs/PoseStamped
    /vrpn_client_node/{vicon_obj}/twist geometry_msgs/TwistStamped


Drone Specific
~~~~~~~~~~~~~~

.. code-block:: yaml

    /mavros/cmd/arming              mavros_msgs/CommandBool
    /mavros/cmd/takeoff             mavros_msgs/CommandTOL
    /mavros/cmd/land                mavros_msgs/CommandTOL
    /mavros/set_mode                mavros_msgs/SetMode
    /mavros/setpoint_position/local geometry_msgs/PoseStamped
    /mavros/cmd/set_home            mavros_msgs/CommandHome


Car Specific
~~~~~~~~~~~~

.. code-block:: yaml

    /ackermann_cmd ackermann_msgs/AckermannDriveStamped
