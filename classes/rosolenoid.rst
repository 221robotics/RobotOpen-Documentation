ROSolenoid
==================

ROSolenoid allows for control of the solenoid outputs on the RobotOpen board. Solenoids are either 12V or 24V and can be set in either a high or low state.


Constructor
-----------------
.. cpp:class:: ROSolenoid(uint8_t channel)

   Creates an ROSolenoid instance with the given solenoid channel (the first channel typically being 0).


Functions
-----------------

.. cpp:function:: void on()

   Applies power to the specified solenoid.

.. cpp:function:: void off()

   Disables power to the specified solenoid.


Examples
-----------------
::

	// create an ROSolenoid object on channel 2
	ROSolenoid giantArm(2);

	// turn the giant arm on!
	giantArm.on();
