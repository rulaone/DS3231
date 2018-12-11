# Ds3231 RTC 

## Table of Contents
1. [Introduction](#introduction)
2. [Bill of Materials and Budget](#bill-of-Materials-and-Budget)
3. [Time Commitment](#time-Commitment)
4. [Mechanical Assembly](#mechanical-Assembly)
5. [PCB and Soldering](#pCB-and-Soldering)
6. [Power Up](#power-Up)
7. [Unit Testing](#unit-Testing)
8. [Production Testing](#production-Testing)

![IMG_5353](https://raw.githubusercontent.com/rulaone/DS3231/master/IMG_5353.JPG)
# Introduction 

This project which is done by connecting the raspberry pi to a ds3231 rtc which give you the date and time. Using the following instruction from buying the parts that is needed to have, how long it take to finish each part,how you can setup the connection, what you need to know about  the power up and unit testing. Most of the work was done in the lab, 


# Bill of Materials and Budget

The materials that I used in my project, most of it I used but there are some materials I did not, also all the products that I bought was from Amazon,it took about one day to be shipped. Starting with the first product which was the raspberry pi, it cost me about $69.99+Tax. the second and the thir item were LCD Display Module it cost about $12.28+Tax, and Lithium battery which was about $8.19+Tax  I did not need to used these items in my project. The fourth item was the Ds3231 RTC the price of it $9.99+Tax,For the tools that I already have was the tool kit which include the jumper wires, Female-to-male Dupont wire and solderless wire and that cost me about $23.99+Tax. In total the price that I used in project without the two items was about $117.49 including Tax.Link to the whole budget[budget](https://github.com/rulaone/DS3231/blob/master/documentation/budget%20.docx).
link for the parts: 
[ds3231 RTC](https://www.amazon.ca/Robojax-DS3231-Precision-Module-Arduino/dp/B07GGM2WZF/ref=sr_1_6?ie=UTF8&qid=1544497739&sr=8-6&keywords=ds3231+rtc)
[Raspberry pi](https://www.amazon.ca/CanaKit-Raspberry-Power-Supply-Listed/dp/B07BD3WHCK/ref=sr_1_5?s=electronics&ie=UTF8&qid=1544497837&sr=1-5&keywords=canakit+raspberry+pi+3+b%2B)

# Time Commitment

The time commitment for ordering the parts all of them it took about a day. Setting up the connection of the circute it should take about a day to get it, getting the i2c detect  about two hours.  Also the time it took me to get the date and time was 4 hours, but making the case to for the project it took me around4 times to do it in three days 

# Mechanical Assembly
 
  Using [Corel](https://www.coreldraw.com/en/pages/free-download/) which you can download it, but it is only 15 days free then you have to purches it, you can download how I have it from here [Rula%2016](https://github.com/rulaone/DS3231/blob/master/Rula%2016.cdr) 
  
  <img src="https://raw.githubusercontent.com/rulaone/DS3231/master/Corel.PNG">
  
  The finall look of the raspberry pi with ds3231 rtc in the case from different sides: [top](https://raw.githubusercontent.com/rulaone/DS3231/master/top.JPG) [back](https://raw.githubusercontent.com/rulaone/DS3231/master/back.JPG) [left](https://raw.githubusercontent.com/rulaone/DS3231/master/left.JPG) [right](https://raw.githubusercontent.com/rulaone/DS3231/master/right.JPG)



# PCB and Soldering

Using this table to connect ds3231 rtc to my raspberry pi:

| Ds3231 | Raspberry Pi |
| --- | --- |
| GND | P1-06 |
| Vcc | P1-01(3.3V) |
| SDA | P1-03(I2C SDA) |
| SCL | 1-05(I2C SCL) |

Also you refer to this link to make sure that the connection of the raspberry pi is right [GPIO](https://www.raspberrypi.org/documentation/usage/gpio/)

By finishing the connection it should look like and make sure you do not leave the workstation powered up close everything you have so don't get ... 
<img src="https://raw.githubusercontent.com/rulaone/DS3231/master/IMG_5273.JPG" hight ="200">

BY using Fritzing which it will help you to get your PCB design done, by click on this link and download [fritzing](http://fritzing.org/download/)and it should look like this :

<img src="https://raw.githubusercontent.com/rulaone/DS3231/master/Fritzing.PNG">

The final look of the PCB design and it is soldered with the headers:

<img src= "https://raw.githubusercontent.com/rulaone/DS3231/master/PCBHeader.JPG">

# Power Up
The connection that you need to detect the right address for ds3231 is (68), by running this command (sudo i2cdetect -y 1), in the below picture the UU means that you are using that address which is 68:

<img src="https://raw.githubusercontent.com/rulaone/DS3231/master/i2cdetect.PNG">

The following picture shows how the ds3231 was connecting to raspberry pi using the PCB board [IMG_5353](https://raw.githubusercontent.com/rulaone/DS3231/master/IMG_5353.JPG)




# Unit Testing

To make sure you have that right set up and the leatest update for the ds3231 follow these steps:
1- sudo apt-get update
2- sudo apt-get upgrade
3-to check if the rtc-ds1307 is there, which it should be done in the system file by: 
sudo nano /etc/modules.
If it is not there then add (rtc-ds1307)to it, then you can save it, use CTRL-X and enter.
shutdown the raspberry pi using the command (sudo halt) and remove the power.

The next step is to setup the i2c using the following commands which will have the acess to the address :
1- sudo nano /etc/rc.local
you need to add the following lines before the exit 0 
echo ds1307 0x68 > /sys/class/i2c-adapter/i2c-1/new_device 
hwclock -s 

<img src="https://raw.githubusercontent.com/rulaone/DS3231/master/code.PNG">

The Hwclock is a program which help you to write to the RTC click on this link to see how does it work [hwclock](https://linux.die.net/man/8/hwclock)
Save and quit using CTRL-X, Y and enter, reboot the raspberry pi using the command (sudo reboot)

The Reaings for the date and time, whcih is done by the following:
  You can read the raspberry pi time:
  ````
  date
  ````
  You can set the system time by:
  ````
    sudo date -s "29 Aug 1997 13:00:00"
  ````
  When you have it correctly you can write the system date and time to the ds3231 RTC  
  ````
  sudo hwclock -w
  ````
  And you should be able to read the date and time back from the ds3231 RTC
  ```
  sudo hwclock -r
  ```
  You can use the semi-colon so that you can read from both times which is the system time and ds3231 RTC 
  <img src="https://raw.githubusercontent.com/rulaone/DS3231/master/DS3231connection.PNG">
  
  # Production Testing
 
