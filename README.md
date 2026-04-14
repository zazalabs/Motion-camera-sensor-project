# Motion-camera-sensor-project

HARDWARE USED:
Raspberry pi 5
Grove 4-pin Female Jumper to Grove 4-pin Conversion Cable
Mini camera cable
Camera module 3 
Grove - PIR Motion Sensor

PROJECT DESCRIPTION:
I created a secuirty system built for the RPI5, using the camera module 3 and a PIR Motion Sensor. Unlike standard camera software programs that recordcs 24/7, this project uses hardware triggers to capture images only when motion is detected. This approach minimizes CPU overhead and saves storage space, whilst capturing key images.

LABORATORY NOTES AND TROUBLESHOOTING:
1.Hardware-level timing (Timeout bug)
During inital testing, the camera frequently reported Device timeout detected
Solution: Increassed the warm-up delay to -t 100 and added the immediate flag to bypass unnecessary frame processing

2. GPIO Zero and the RPI Quirk
The pi 5 introduces the RPI/O controller, which handles GPIO pins differently than previous models.
Solution: Migrated from "Event-Driven" code to a "Polling Loop" using a while True statement. This bypasses the buggy backlground threading in current gpiozero versions on the pi 5.

3. Syntax and pathing
   Syntax: Grove sesors require pull_up=False to allow the sensor to manage its own electrical signal.
   Solution: Resolved "failed to open file" errors by using os.path.expanduser("~") to dynamically locate the user's  Home directrory rather than hard-coding /home/pi/.
