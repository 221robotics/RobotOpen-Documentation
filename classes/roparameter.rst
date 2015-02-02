ROParameter
==================

ROParameter allows for on-the-fly configuration of your RobotOpen controller from the dashboard. ROParameters are variables that can be modified straight from the driver station without recompiling and flashing robot code. Supported classes: ROBoolParameter, ROCharParameter, ROIntParameter, ROLongParameter, ROFloatParameter. Note that your robot must be disabled for this values to be updated from the driver station.


Constructors
-----------------
.. cpp:class:: ROCharParameter(String label, uint8_t id)

   Creates an ROCharParameter instance with the given id. Note that no two parameters may have the same id.

.. cpp:class:: ROIntParameter(String label, uint8_t id)

   Creates an ROIntParameter instance with the given id. Note that no two parameters may have the same id.

.. cpp:class:: ROLongParameter(String label, uint8_t id)

   Creates an ROLongParameter instance with the given id. Note that no two parameters may have the same id.

.. cpp:class:: ROFloatParameter(String label, uint8_t id)

   Creates an ROFloatParameter instance with the given id. Note that no two parameters may have the same id.


Functions
-----------------

.. cpp:function:: [char, int, long, float] read()

   Returns the current stored value for the parameter, depending upon the class used.


Examples
-----------------
::

	// create parameter objects
	ROFloatParameter pConstant("pconstant", 0);
	ROFloatParameter iConstant("iconstant", 1);
	ROFloatParameter dConstant("dconstant", 2);

	// use parameters as PID constants
	void loop() {
		runPID(pConstant.get(), iConstant.get(), dConstant.get());
	}