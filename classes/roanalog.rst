ROAnalog
==================

ROAnalog gives you access to the analog inputs on your RobotOpen board.


Constructor
-----------------
.. cpp:class:: ROAnalog(uint8_t channel)

   Creates an ROAnalog instance with the given analog channel (the first channel typically being 0).


Functions
-----------------

.. cpp:function:: int read()

   Read the samples value that can range from 0-1023 (typically proportional to 0-5V).


Examples
-----------------
::

	// create an ROAnalog instance on analog channel 1
	ROAnalog steerPOT(1);

	// get current reading (0-1023)
	int read();