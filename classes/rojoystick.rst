ROJoystick
==================

ROJoystick provides access to any controller or joystick data transmitted by the driver station. ::



	ROJoystick usb1(1);


	byte usb1.leftX();
	byte usb1.leftY();
	byte usb1.rightX();
	byte usb1.rightY();
	boolean usb1.btnA();
	boolean usb1.btnB();
	boolean usb1.btnX();
	boolean usb1.btnY();
	boolean usb1.btnLShoulder();
	boolean usb1.btnRShoulder();
	byte usb1.lTrigger();
	byte usb1.rTrigger();
	boolean usb1.btnSelect();
	boolean usb1.btnStart();
	boolean usb1.btnLStick();
	boolean usb1.btnRStick();
	boolean usb1.dPadUp();
	boolean usb1.dPadDown();
	boolean usb1.dPadLeft();
	boolean usb1.dPadRight();
	byte usb1.auxOne();
	byte usb1.auxTwo();
	byte usb1.auxThree();
	byte usb1.auxFour();