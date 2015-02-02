ROEncoder
==================

ROEncoder provides access to the quadrature encoder inputs on your RobotOpen board. Using ROEncoder, the number of interrupts on each quad input can be read.


Constructor
-----------------
.. cpp:class:: ROEncoder(uint8_t channel)

   Creates an ROEncoder instance with the given encoder channel (the first channel typically being 0).


Functions
-----------------

.. cpp:function:: long read()

   Returns the current 32 bit value of the encoder count.

.. cpp:function:: long write(int32_t new_value)

   NOTE: Sasquatch boards only. Sets the encoder count to a new value.

.. cpp:function:: void reset()

   NOTE: Gorgon boards only. Resets the encoder count to 0.

.. cpp:function:: float readCPS()

   NOTE: Gorgon boards only. Returns the current number of counts per second.

.. cpp:function:: void setSensitivity(uint16_t sensitivity)

   NOTE: Gorgon boards only. Used to adjust how often the coprocessor recalculates encoder counts and CPS. By default this is set to 4 samples. If you have an encoder that generates a very large number of counts per rotation (greater than a couple hundred), you may want to experiment with raising this number.

.. cpp:function:: void setCPSSamplesToAverage(uint8_t samples)

   NOTE: Gorgon boards only. Sets the number of samples used in the averaging of the CPS value. Larger numbers will react less quickly, while lower numbers will be jumpier. The default is set to 9.


Examples
-----------------
::

	// create an encoder object
	ROEncoder leftDriveEncoder(1);

	// read the encoder count
	long mycount = leftDriveEncoder.read();