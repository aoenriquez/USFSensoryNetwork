# USFSensoryNetwork
A collaborative project by myself and fellow USF College of Computer Science and Engineering students to provide useful analytics in regards to health worker hand cleanliness

Functional Description
_________________________________________________________________
	Preventing the spread of nosocomial infections is a high priority for all health care facilities. When a health care worker enters a patient’s room they’re required to wash-in and wash-out, but often they are in a hurry and they forget about this requirement. The primary objective of our project design is to help workers remember to properly sanitize their hands, thus mitigating the spread of harmful bacteria. Additionally, the ability to track and compare usages statistic accomplishes the following goals:
Increased accountability for health care workers maintaining cleanliness standards
Provide helpful, quantifiable metrics to monitor for the purpose of providing ideal cleanliness standards for patient safety

	The Tech Arrangers are developing a system that detects when a worker enters a room through the use of a passive infrared (PIR) motion sensor, this will be stored as a separate log entry.  A strobe light will light up and once an employee is finished up in the bathroom, they will use an RFID reader to dispense soap and deactivate the strobe light, simply by putting up an ID card to the soap dispenser.  This will ensure that the employee washes their hands with the proper steps and not a simple rinse. The RFID proximity reader will identify the person and send that information to the Raspberry Pi where a script will pick-up the input and store that data as an excel spreadsheet.  Supplementally, the logs will then be used to track the activity of the healthcare professional, to provide transparent data for the purpose of compliance to standards, as well as output being sent to Nagios, an open source monitoring software that utilizes StatsD utility in Unix systems.  With both the time of entry and soap dispensing being monitored, the cleanliness of each individual can be monitored closely by authoritative individuals  
	For afford ability purposes, our capital will not make many components possible, RFID cards, or proximity readers. We will, however, have a PIR motion sensor that connects to our Raspberry Pi and we will develop software that will process input from the sensor. 

Components 

Functional Components 
PIR MotionSensor to detect basic movement; May have one on soap dispenser to simulate RFID and to show the processing of two different log entries. 
 Raspberry Pi 3 to process the information and allocate it to the proper services.
LED strobe light to signal the employee
Soap dispenser 
Badge to trigger motion sensor and simulate RFID Badge 

Expected Components 
All components above are expected in the final product.

Stretch Components 
Fully functional RFID badges would be realized if we had the proper applications for the transfer of data.
A fully operational monitoring system.  We do not have the networking to show a functional monitoring application that can be used on a large scale for a hospital. With enough time we might have a tech demo but we will focus on the sensory groundwork first. 

Hardware Objectives
PIR MotionSensor True condition will send “detected” message to Pi.
Script then sends signal that activates light to remind employee to wash-in.
Worker goes to sink area and scans RFID card on soap dispenser and presumably washes hands.
Once RFID card data is received by Pi, 2 events occur:
	1) Light extinguishes
	2) Employee data is sent to Pi.
Script will send employee data to a log.

Below is an overview of both abstract hardware and actual hardware:

Abstract equipment includes RFID proximity reader and strobe light.

Software Components
______________________________________________________________________
Software Use-Case: The software use case as a supplement to physical hardware shall be outlined as follows: A Debian kernel OS to be decided on after initial hardware specifications are analyzed, Python compilers and dependencies will be installed and configured on host OS, although the requirement for scripts also being composed in BASH (Bourne Again Shell) may be of further use if the python libraries do not support piping metrics to our monitoring software. Subsequently, our metrics that are recorded will be passed through StatsD communication port 5777 on the host OS using NRPE protocols to a web application hosted on the Raspberri Pi for analytics purposes. Finally, Arduino may be required for use in the RFID and PIR components, however, their support depends on firmware which does not fit this initial use case at this time. It has been included for possible solutions regarding firmware.

Codebase:  Our Code base will be stored in GitHub repositories, with tracking provided in our commits channel in the team slack client. Additionally, all Git logs and pull requests will be logged for tracking contribution.
