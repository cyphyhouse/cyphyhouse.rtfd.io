===================
Configuration Files
===================

Example configuration file

.. code-block:: yaml

    agents:
        - pid: 1
          bots: 3
          rip: 127.0.0.1
          rport: 2001
          plist: [2002, 2003]
          mutex_handler: BaseMutexHandler
        - pid: 2
          bots: 3
          rip: 127.0.0.1
          rport: 2002
          plist: [2001, 2003]
          mutex_handler: BaseMutexHandler
        - pid: 3
          bots: 3
          rip: 127.0.0.1
          rport: 2003
          plist: [2001]
          mutex_handler: BaseMutexHandler

    motion_automaton:
        - bot_name: drone1
          bot_type: QUAD
          waypoint_topic:
            name: waypoint
            type: geometry_msgs/PoseStamped
          reached_topic:
            name: reached
            type: std_msgs/String
          positioning_topic:
            name: /vrpn_node/drone1/pose
            type: geometry_msgs/PoseStamped
          path_planner: SimplePlanner


        - bot_name: car1
          bot_type: CAR
          waypoint_topic:
            name: waypoint
            type: geometry_msgs/PoseStamped
          reached_topic:
            name: reached
            type: std_msgs/String
          positioning_topic:
            name: /vrpn_node/car1/pose
            type: geometry_msgs/PoseStamped
          path_planner: SimplePlanner


.. todo::

    The options are from looking into ``AgentConfig.py``.
    We could simply the options for configuration files and generate necessary
    objects after parsing.

    E.g., ``bots`` and ``mutex_handler`` should be moved out and shared by
    all agents.

    ``plist`` can be as simple as a list of pids of other agents.


