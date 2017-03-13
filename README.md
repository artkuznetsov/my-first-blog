#Introduction

This document will be useful for configuration of uploading and downloading publishers and adUnits from database.

#Enviroment

For uploading and downloading you should have:

1. Python3.
	brew install python3
2. For Linux and Mac OS:

	unixODBC:

		brew install unixodbc

	FreeTDS driver (with ODBC):
	
		brew install freetds --with-unixodbc)

#Configuring

After this you should configure FreeTDS driver:

1. create tds.driver.template file with this text:

		[FreeTDS]
		Description = v0.63 with protocol v8.0
 		Driver      = /usr/local/lib/libtdsodbc.so
	
	Note: enter "Driver = <path_to_libtdsodbc.so>" for your libtdsodbc.so file location.

2. follow this commands:
	
	cd <path_to_tds.driver.template_file>

	sudo odbcinst -i -d -f tds.driver.template 


Replace SQL driver on FreeTDS fo Linux/Mac OS.
	
1. Open file dataswitch/db.py with help an any text editor.
	
in the function	def make_conn_string() replace the variable driver on "FreeTDS".


For install an additional packs you can just follow this command:
	
	pip3 install -r requirements.txt


Now, if you want to download adn AdUnits from DB, you can enter this command:
	
	python3 dum-adunit.py
	
After this you can see this mesage (in the succesfuly case):
	
	"DONE: adunits are saved to dump-adunits.csv"

You can edit some fields, save this file as adunits.csv and run upload-adunits.py script:
	
	pyhton3 upload-adunits.py
	"DONE: Processed [X] ad units"

For editing publishers you can follow at the same flow like fod aduints.

