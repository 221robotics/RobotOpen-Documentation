ROParameter
==================

ROParameter allows for on-the-fly configuration of your RobotOpen controller from the dashboard. ROParameters are variables that can be modified straight from the driver station without recompiling and flashing robot code. Supported types: BOOL, CHAR, INT, LONG, FLOAT. ::



	// DS label, variable type, UNIQUE address (0 through 99)
	ROParameter pConstant("pconstant", FLOAT, 0);
	ROParameter iConstant("iconstant", FLOAT, 1);
	ROParameter dConstant("dconstant", FLOAT, 2);


	void loop() {
		runPID(pConstant.getFloat(), iConstant.getFloat(), dConstant.getFloat());
	}