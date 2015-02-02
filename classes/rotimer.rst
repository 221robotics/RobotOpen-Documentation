ROTimer
==================

ROTimer allows for simple time-based loop execution and delays. By utilizing ROTimer, a certain portion of code can be run at a specific speed (processor time permitting) or "ready'd" for execution.


Constructor
-----------------
.. cpp:class:: ROTimer

   Creates an ROTimer instance.


Functions
-----------------

.. cpp:function:: void queue(uint16_t milliseconds)

   Schedule the timer to expire within the number of milliseconds specified.

.. cpp:function:: boolean ready()

   Returns true if the timer has expired, false otherwise.


Examples
-----------------
::

	// create timers
	ROTimer step1;
	ROTimer step2;
	ROTimer step3;
	ROTimer repeatingLoop;

	void setup() {
		// schedule timers to fire immediately
		step1.queue(0);
		repeatingLoop.queue(0);
	}


	void loop() {
		if (step1.ready()) {
			// do something
			step2.queue(1000);
		}
		if (step2.ready()) {
			// do something else
			step3.queue(2000);
		}
		if (step3.ready()) {
			// last step of the process, now repeat
			step1.queue(0);
		}

		if (repeatingLoop.ready()) {
			// do something every 1000ms
			repeatingLoop.queue(1000);
		}
	}