ROAnalog
==================

ROAnalog gives you access to the analog inputs on your RobotOpen board. ::



	ROAnalog steerPOT(1);


	// get current reading (0-1023) proportional to 0-5V
	int read();