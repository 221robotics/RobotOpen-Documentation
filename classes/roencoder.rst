ROEncoder
==================

ROEncoder provides access to the quadrature encoder inputs on your RobotOpen board. Using ROEncoder, the number of interrupts on each quad input can be read. ::



	ROEncoder leftDriveEncoder(1);


	leftDriveEncoder.reset();
	leftDriveEncoder.getTicks();