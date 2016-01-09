# maxsonar
Scripts to interact with the Maxbotix HRLV-MaxSonar-EZ sensors over serial

The Maxbotix HRLV-MaxSonar-EZ ultrasonic rangefinder is a nice little device that works well with the Raspberry Pi due to its having serial output. Although it's also got analog output and PWM output, the serial gives a direct reading within the device's 300-5000mm range, giving better precision than a 12-bit A2D conversion. This serial data is in a stream in the following format:

R####\rR####\rR####\r...

Where "####" is the rangefinder reading in mm. The update rate is approximately 4Hz.

This script reads 65 bytes from the serial, then processes the output, giving an average over 10 readings. If there aren't any valid readings, it gives no output.
