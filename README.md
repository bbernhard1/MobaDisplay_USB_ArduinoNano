## This is a Arduino Project to drive a Platform-Clock and/or Platform-Train-Departure-Display
Previously both dispalys where available as dedicated projects, now both had bene combined in one universal code.
At the mmoment the code is configured to drive both display type at teh same time. With minor change it can reconfigured to support two or more displays of same type.
Im subfolder ./script befinden sich zwei Powershell Scripte um beie Displayvarianten zu anzusteuern. 

The interface to iTrain is done with powershell scripts which are called from iTrain actions. 


Parameters accepted by the setClockDisplay Script:
'T' System   	... set the display to system time of the host computer, there MUST be a space after the 'T'
'T' 16:31    	... set the display to to given time, in thsi case 16:31, there MUST be a space after the 'T'
'S' 			... increment the time by by one minute

The sketch does only provide a static display, there is no realtime clock function included. 
This is to support the time scaling function from iTrain. To get the dispaly synchronized 




Parameter accepted by the setPlatformDisplay Script:
The script accepts four subsequent parameters, parameters are separated by space 
Parameter1 First line. Train name
Parameter2 second line eg. first destination
Parameter3 third line eg. second destination
Parameter4 departure time
For german "umlauts" their representive must be used eg. "ae" instead of "ä"
eg setPlatformDisplay1.ps1 IEC123 Muenich Salzburg 13:30

Spaces within one parameter must be escaped by apostrophs.
eg setPlatformDisplay1.ps1 IEC123 Muenich 'ueber Salzburg' 13:30

![image](https://user-images.githubusercontent.com/10500682/143779301-96a357a8-8333-43ef-9490-4cd121c700d1.png)
