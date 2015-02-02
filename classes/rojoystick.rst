ROJoystick
==================

ROJoystick provides access to any controller or joystick data transmitted by the driver station.

Constructor
-----------------
.. cpp:class:: ROJoystick(uint8_t joystick_number)

   Creates an ROJoystick instance with the given joystick number. This can range from 1 to 4 and is mapped in the driver station.


Functions
-----------------

.. cpp:function:: byte leftX()

   Returns a value from 0-255 representing the position of the left joystick's X axis.

.. cpp:function:: byte leftY()

   Returns a value from 0-255 representing the position of the left joystick's Y axis.

.. cpp:function:: byte rightX()

   Returns a value from 0-255 representing the position of the right joystick's X axis.

.. cpp:function:: byte rightY()

   Returns a value from 0-255 representing the position of the right joystick's Y axis.

.. cpp:function:: boolean btnA()

   Returns true if button A is held. False otherwise.

.. cpp:function:: boolean btnB()

   Returns true if button B is held. False otherwise.

.. cpp:function:: boolean btnX()

   Returns true if button X is held. False otherwise.

.. cpp:function:: boolean btnY()

   Returns true if button Y is held. False otherwise.

.. cpp:function:: boolean btnLShoulder()

   Returns true if the left shoulder is held. False otherwise.

.. cpp:function:: boolean btnRShoulder()

   Returns true if the right shoulder is held. False otherwise.

.. cpp:function:: byte lTrigger()

   Returns a value from 0-255 (hardware permitting) representing the pressure on the left trigger.

.. cpp:function:: byte rTrigger()

   Returns a value from 0-255 (hardware permitting) representing the pressure on the right trigger.

.. cpp:function:: boolean btnSelect()

   Returns true if the select button is held. False otherwise.

.. cpp:function:: boolean btnStart()

   Returns true if the start button is held. False otherwise.

.. cpp:function:: boolean btnLStick()

   Returns true if the left stick is pushed down. False otherwise.

.. cpp:function:: boolean btnRStick()

   Returns true if the right stick is pushed down. False otherwise.

.. cpp:function:: boolean dPadUp()

   Returns true if the D-Pad up button is held. False otherwise.

.. cpp:function:: boolean dPadDown()

   Returns true if the D-Pad down button is held. False otherwise.

.. cpp:function:: boolean dPadLeft()

   Returns true if the D-Pad left button is held. False otherwise.

.. cpp:function:: boolean dPadRight()

   Returns true if the D-Pad right button is held. False otherwise.

.. cpp:function:: byte auxOne()

   Returns a value from 0-255 for the aux 1 channel. Note: This allows for future expansion within the RobotOpen protocol. Custom joystick implementations could send this.

.. cpp:function:: byte auxTwo()

   Returns a value from 0-255 for the aux 2 channel. Note: This allows for future expansion within the RobotOpen protocol. Custom joystick implementations could send this.

.. cpp:function:: byte auxThree()

   Returns a value from 0-255 for the aux 3 channel. Note: This allows for future expansion within the RobotOpen protocol. Custom joystick implementations could send this.

.. cpp:function:: byte auxFour()

   Returns a value from 0-255 for the aux 4 channel. Note: This allows for future expansion within the RobotOpen protocol. Custom joystick implementations could send this.


Examples
-----------------
::

	// create a reference to joystick #1
	ROJoystick usb1(1);

	// get the position of the left joystick's x axis
	byte = usb1.leftX();

	// get the button status of button A
	bool btnA = usb1.btnA();