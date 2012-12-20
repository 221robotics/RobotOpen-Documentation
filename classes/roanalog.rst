ROAnalog
==================

ROAnalog gives you access to the analog inputs on your RobotOpen board. ::



	ROAnalog steerPOT(1);


	// indepdendent of base voltage
	readVoltage(); 	// (0-5)
	readRaw(); 		// (0-1023)

	// set base voltage
	setBaseVoltage(3.3);

	// based off base voltage (by default 5.0V)
	readPercentage(); 	// (0-100 of base)
	readScaled(); 		// (0-1023 of base)