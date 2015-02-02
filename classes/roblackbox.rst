ROBlackBox
==================

ROBlackBox offers SD card based logging at regular intervals for later analysis. NOTE: This class is only available on the Sasquatch robot controller.


Functions
-----------------

.. cpp:function:: void ROBlackBox.log(String data)

   Log the given string to the SD card.


Examples
-----------------
::

	// log "some info" to the SD card
	ROBlackBox.log("some info");