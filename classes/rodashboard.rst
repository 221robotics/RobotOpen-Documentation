RODashboard
==================

RODashboard allows for arbitrary data transmission to the dashboard to de displayed, graphed, or saved in real time. Variables can either be sent over or debug messages to be displayed on the virtual console. ::



	RODashboard.publish("name", variable);

	RODashboard.console("this is a debug statement");