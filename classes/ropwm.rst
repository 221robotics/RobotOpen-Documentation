ROPWM
==================

ROPWM allows for control of the PWM outputs on the RobotOpen board. Pulse width modulation is frequently used for electronic speed controllers (ESC) or servos. ::



	ROPWM leftDrive(2);


	leftDrive.write(127);
	leftDrive.disable();