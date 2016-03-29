# toybox-rpi
Raspberry PI incarnation of the Internet Toybox audience-controlled stage effects system

# From toyboxrpi-setup.txt

Internet Toybox Raspberry PI Version ("toyboxrpi")
In development as of 03-29-16 @diemastermonkey
Preliminary setup notes
-----------------------------------------------
Test unit: Raspberry PI Version A

PI Setup
-----------------------------------------------
1. Install Raspian (lite is fine)
2. Ensure Java is installed and operational
3. Install/configure/test pi-blaster

   https://github.com/sarfata/pi-blaster
   
4. Connect peripherals to your PI's GPIO pins

Toybox Setup
-----------------------------------------------
1. Install toybox binaries and stuff (on PI)

   mkdir /opt/toyboxrpi
   
   cp ToyboxRPI.jar /opt/toyboxrpi
   
   cp toybridge.cfg /opt/toyboxrpi

   ...or build from source (pending)
   
2. Configure toybridge.cfg
 

   vi /opt/toyboxrpi/toybridge.cfg
   
   See _URL_ for videos

Test Toybox
-----------------------------------------------
1. Log-in to your chat channel, so you can see
   the toybox when it logs-on. On the PI, start
   toybox:

     cd /opt/toyboxrpi
     
     java -jar ToyboxRPI.jar

   You should see the toybox announce itself in chat.
   If not, check the console for error messages, and
   probably adjust the configuration file.

2. Try some low-level commands in the chat venue

   Example: I have GPI pin 18 connected to a servo.

     18=0.15;
     
     18=0.53;

   ...should move the servo to 15% and 53% of its range.
   If the commands have no effect, check the console.

Connect Your Chatbot
-----------------------------------------------
1. Make sure your chatbot is listed on the
   "bridge_peers" configuration option

2. Add a high-level command to your chatbot

   Example: I still have GPIO 18 connected to a servo.

   Chatbot command:    !servoleft  
   
   Chatbot response:   18=0.15; 

   Don't forget, low-level commands must end with a semicolon!

3. Save command and test by typing in your chat venue:

      !servoleft

   The chatbot should respond with the low-level syntax, which
   the toybridge will process. If not, check the console output. 

Additional Notes
-----------------------------------------------
Currently disused but optional

   https://github.com/Pi4J/pi4j/

   Optional/disused:
   
   For node.js https://github.com/sarfata/pi-blaster.js
