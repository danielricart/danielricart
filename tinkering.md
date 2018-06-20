* Tinkering ring ring *

Some fast notes about tinkering.
Raspberry pi with a cheap temperature and humidity sensor (DHT11)
I sketched a fast python module and script that polls the sensor 80 times at the default rate (1 every 2s) and plots a graph.
See the code here.

DHT11, and his sibling DHT22 are cheap and good enough for experimenting but they are not very reliable. I'd not bet my heating on its hands...
A better and more reliable device is made by Bosch and it uses i2c for communication instead of a  GPIO. GY-BME280 is more reliable and uses i2c. It costs 10$ at most. 

Here you can find a scientific comparison of several cheap temperature and humidity sensors: http://www.kandrsmith.org/RJS/Misc/Hygrometers/calib_many.html
