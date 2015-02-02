RobotOpen
==================

The RobotOpen class is the primary class that manages connectivity, loop scheduling, and general operation of the robot. A single instance of this class is created automatically and can be accessed statically.


Functions
-----------------

.. cpp:function:: void RobotOpen.setIP(IPAddress newIP)

   This should be called only once in the setup function of the robot code. It changes the robot's default IP of 10.0.0.22 to the given IP address. The IPAddress format is given as 4 comma delimited values. For example: RobotOpen.setIP(192,168,1,22)

.. cpp:function:: void RobotOpen.setTimeout(int timeout_in_ms)

   By the default the robot will consider itself disabled when a packet has not been received in a period greater than 200 milliseconds. This can be overridden using this function by defining the number of milliseconds until the robot is disabled.

.. cpp:function:: void RobotOpen.begin(*enabledCallback, *disabledCallback, *timedtasksCallback)

   This function should be called once in the setup function of the robot code with a reference to an enable function, disable function, and timed tasks function. The enabled function is only called when the robot is enabled. The disabled function is only called when the robot is disabled. Timed tasks will execute continuously while the robot is powered on.

.. cpp:function:: void RobotOpen.syncDS()

   This is used internally by the RobotOpen library to process data and keep the robot operational. This is the only call that should be in your Arduino loop() function. It should not be called anywhere else.

.. cpp:function:: int RobotOpen.numJoysticks()

   Returns the number of joysticks currently being sent from the driver station.