RODigitalIO
==================

RODigitalIO provides access to the digital pins on your RobotOpen board. Pins can either be configured as inputs or outputs. When a pin is configured as an input, it will be read as either a high or low state. When configured as an output, the pin can be set either high or low. A low state will generate a voltage of 0V. A high state will generate a 5V signal on that pin.


Constructor
-----------------
.. cpp:class:: RODigitalIO(uint8_t channel, uint8_t mode)

   Creates an RODigitalIO instance with the given digital channel (the first channel typically being 0). The second parameter can either be INPUT or OUTPUT.


Functions
-----------------

.. cpp:function:: void on()

   OUTPUT only. Toggle the OUTPUT high.

.. cpp:function:: void off()

   OUTPUT only. Toggle the OUTPUT low.

.. cpp:function:: boolean read()

   INPUT only. Returns true if the input read is high, otherwise returns false.

.. cpp:function:: void pullUp()

   INPUT only. Uses the Arduino's internal pull-up resistor to drive the line to 5V by default.

.. cpp:function:: void allowFloat()

   INPUT only. Disables the pullup resistor, if enabled.

.. cpp:function:: void setMode(uint8_t mode)

   Change the mode of the digital pin. Can be either INPUT or OUTPUT.


Examples
-----------------
::

	// create some objects
	RODigitalIO redLED(3, OUTPUT);
	RODigitalIO blueButton(2, INPUT);

	// output calls
	redLED.on();

	// input calls
	blueButton.pullUp();
	bool is_held = blueButton.read();
	blueButton.allowFloat();

	// make blueButton an output
	blueButton.setMode(OUTPUT);