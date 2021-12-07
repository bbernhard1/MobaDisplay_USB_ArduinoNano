## This Arduino Project is to be used with iTrain Model Railroud control software. 
#### It can drive a model Platform-Clock and/or Platform Train-Departure-Display.
Previously both display where available as dedicated projects, now both had been combined in one universal code. </br>
The connection to the host computer is via USB COM port. Which allows definition of the display content. </br>
A re implementatin of the telnet link which is known from previous project is in work. Furthermore a MQTT link is in preparation.
At the moment the code is configured to drive both display type at the same time. It is already prepared to to support two or more displays of same type.  
This will also added at a later state. </br>
Here is an sample how the result looks like. - Ideas for a nice 3D printed housing are welcome - 

![PlatformDisplay](https://user-images.githubusercontent.com/10500682/143893848-ba484191-0319-47d4-91c9-c8e92d3ffb47.jpg)

The interface to iTrain is done with powershell scripts which are called from iTrain actions or standalone from any other trigger. </br>
##### Some sample scripts an be found in the ./script subfolder of this Github project.
***
#### Platform Clock:
Parameters accepted by the setClockDisplay.ps1 Script:
* T System   	... set the display to system time of the host computer, there MUST be a space after the 'T'
* T 16:31    	... set the display to to given time, in this case 16:31, there MUST be a space after the 'T'
* S 			... increment the time by by one minute
eg: setClockDisplay.ps1 T 16:31

Since the model time in iTrain can be scaled there is no realtime clock function included. </br> 
The sketch does only provide a static display. Which need to be updated by the host in regular intervalls to get the clock hands moving. </br>
For synchronization with iTrain this action is recomended:
![image](https://user-images.githubusercontent.com/10500682/143782704-4e0a0537-3001-4f7e-9f89-4edbaf517cba.png)
***
#### Platform Display:
Parameter accepted by the setPlatformDisplay.ps1 Script: </br>
The script accepts four subsequent parameters. All parameters need to be separated by a space. 
* Parameter1 First line. Train name
* Parameter2 second line eg. first destination
* Parameter3 third line eg. second destination
* Parameter4 departure time
For german "Umlauts" their representive must be used eg. "ae" instead of "ä"
eg setPlatformDisplay1.ps1 IEC123 Muenich Salzburg 13:30

Spaces within one parameter must be escaped by quotation marks.
eg: setPlatformDisplay1.ps1 IEC123 Muenich 'ueber Salzburg' 13:30

![image](https://user-images.githubusercontent.com/10500682/143779301-96a357a8-8333-43ef-9490-4cd121c700d1.png)
***
The hardware is pretty simple. My prototype use a ARDUINO Micro, but for sure it can run on any other Arduino type microcontroler.
The next version will use a ESP8266 NodeMCU board to support Wifi connection. </br>
The display are cheap OLED display with I2C interface.  
Wireing is straight forward, yust connect the SCL and SDA with any free digital I/O Pin and configure the settings.h accordingly.

**The project is VSCode project with PlatformIO pluggin.**


![image](https://user-images.githubusercontent.com/10500682/144753805-d6ae1f81-f1c7-48d2-8a89-039faec08f1a.png)


