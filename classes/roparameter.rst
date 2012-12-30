ROParameter
==================

ROParameter allows for on-the-fly configuration of your RobotOpen controller from the dashboard. ROParameters are variables that can be modified straight from the driver station without recompiling and flashing robot code. ::



	// DS label, variable type, UNIQUE address (0 through 255)
	ROParameter pConstant('pconstant', float, 0);
	ROParameter iConstant('iconstant', float, 1);
	ROParameter dConstant('dconstant', float, 2);


	void loop() {
		runPID(pConstant.get(), iConstant.get(), dConstant.get());
	}