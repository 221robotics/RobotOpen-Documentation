RODigitalIO
==================

RODigitalIO provides access to the digital pins on your RobotOpen board. Pins can either be configured as inputs or outputs. When a pin is configured as an input, it will be read as either a high or low state. When configured as an output, the pin can be set either high or low. A low state will generate a voltage of 0V. A high state will generate a 5V signal on that pin. ::



	RODigitalIO redLED(3, OUTPUT);
	RODigitalIO blueButton(2, INPUT);


	// output calls
	redLED.on();
	redLED.off();

	// input calls
	boolean blueButton.read();
	blueButton.pullUp();
	blueButton.allowFloat();

	// mode config
	blueButton.setMode(INPUT);