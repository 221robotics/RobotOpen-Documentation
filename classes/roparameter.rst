ROParameter
==================

ROParameter allows for on-the-fly configuration of your RobotOpen controller from the dashboard. ROParameters are variables that can be modified straight from the driver station without recompiling and flashing robot code. Supported classes: ROBoolParameter, ROCharParameter, ROIntParameter, ROLongParameter, ROFloatParameter. ::



	// DS label, UNIQUE address (0 through 99)
	ROFloatParameter pConstant("pconstant", 0);
	ROFloatParameter iConstant("iconstant", 1);
	ROFloatParameter dConstant("dconstant", 2);


	void loop() {
		runPID(pConstant.get(), iConstant.get(), dConstant.get());
	}