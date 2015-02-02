RODashboard
==================

RODashboard allows for arbitrary data transmission to the dashboard to de displayed, graphed, or saved in real time. Variables can either be sent over to be added to the list of values or debug messages can be displayed in the virtual console.


Functions
-----------------

.. cpp:function:: void RODashboard.debug(String data)

   Log the given string to the virtual console.

.. cpp:function:: void RODashboard.publish(String label, byte val)

   Transmit the provided byte with the specified label to the dashboard.

.. cpp:function:: void RODashboard.publish(String label, int val)

   Transmit the provided int with the specified label to the dashboard.

.. cpp:function:: void RODashboard.publish(String label, long val)

   Transmit the provided long with the specified label to the dashboard.

.. cpp:function:: void RODashboard.publish(String label, float val)

   Transmit the provided float with the specified label to the dashboard.


Examples
-----------------
::

	// send over the answer
	int var = 42;
	RODashboard.publish("name", var);

	// log to the console
	RODashboard.debug("this is a debug statement");