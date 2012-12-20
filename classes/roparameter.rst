ROParameter
==================

ROParameter allows for on-the-fly configuration of your RobotOpen controller from the dashboard. ROParameters are variables that can be modified straight from the driver station without recompiling and flashing robot code. ::



	// variable type followed by a UNIQUE address (0 through 1000)
	ROParameter pConstant(float, 0);
	ROParameter iConstant(float, 1);
	ROParameter dConstant(float, 2);


	void loop() {
		runPID(pConstant.get(), iConstant.get(), dConstant.get());
	}