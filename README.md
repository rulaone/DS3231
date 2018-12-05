# Ds3231 RTC 

## Table of Contents
1. [Introduction](#introduction)
2. [Student Sense Hat Specifications](#student-sense-hat-specifications)
3. [Student Sense Hat Electronic Design Files](#student-sense-hat-electronic-design-files)
4. [Student Sense Hat Assembly](#student-sense-hat-assembly)
5. [Student Raspberry Pi Image Creation and Test Code](#student-raspberry-pi-image-creation-and-test-code)
6. [Enterprise Wi-Fi](#enterprise-wi-fi)

![IMG_5353](https://raw.githubusercontent.com/rulaone/DS3231/master/IMG_5353.JPG)
# Introduction 

DS3231 RTC(Real Time Clock) sensro which shows the time and date, by cnnecting it to a Raspberry Pi which is 
is of a hand solderable 
design meant to be compatible with the devices in the Humber Parts Crib which require more skills and techniques to assemble.
It has a bidirectional LED and three I2C device sockets. The bidirectional LED allows the hardware equivalent of "Hello World"
to be achieved by blinking the LED. I2C is a very common hardware peripheral bus and is designed to have an analog breakout
board, a Real Time Clock module, and an integrated environmental sensor module connected. It takes most individuals about a
week of effort to complete these build instructions directed towards technologically inclined students especially given other
commitments. Be aware that the image creation steps take at least 3 hours alone.



Ds3231 rtc is senser which shows time and date, which will be connecting to a raspberry Pi using a PCB design with following connecting :

| Ds3231 | Raspberry Pi |
| --- | --- |
| GND | P1-06 |
| Vcc | P1-01(3.3V) |
| SDA | P1-03(I2C SDA) |
| SCL | 1-05(I2C SCL) |
