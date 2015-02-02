ROStatus
==================

ROStatus provides current robot status such as enabled state, power level, and driver station connection information.


Functions
-----------------

.. cpp:function:: float ROStatus.batteryReading()

   On supported boards, returns the main battery voltage when the BMC jumper is selected.

.. cpp:function:: boolean ROStatus.isEnabled()

   Returns true if the robot is enabled. False otherwise.

.. cpp:function:: int ROStatus.uptimeSeconds()

   Returns the number of seconds that the RobotOpen board has been powered up for.