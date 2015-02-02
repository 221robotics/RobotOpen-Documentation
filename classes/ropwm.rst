ROPWM
==================

ROPWM allows for control of the PWM outputs on the RobotOpen board. Pulse width modulation is frequently used for electronic speed controllers (ESC) or servos. Valid range is between 0-255, 127 being neutral.


Constructor
-----------------
.. cpp:class:: ROPWM(uint8_t channel)

   Creates an ROPWM instance with the given PWM channel (the first channel typically being 0).


Functions
-----------------

.. cpp:function:: void write(uint8_t setpoint)

   Set the PWM channel to the given value. Automatically attaches a PWM channel if detached.

.. cpp:function:: void detach()

   NOTE: Supported on Sasquatch and Gorgon only. Detaches a PWM channel after being attached. This will neutral out most speed controllers and disable servos.

.. cpp:function:: void attach()

   NOTE: Supported on Sasquatch and Gorgon only. Re-attaches a PWM channel after being detached.


Examples
-----------------
::

	// create a left drive ROPWM object on channel 2
	ROPWM leftDrive(2);

	// set it to 200
	leftDrive.write(200);