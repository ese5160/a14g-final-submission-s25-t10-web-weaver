[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/AlBFWSQg)
# a14g-final-submission

    * Team Number: 10
    * Team Name: Web Weaver
    * Team Members: Zhiye Zhang, Yunlong Han
    * Github Repository URL: https://github.com/ese5160/a14g-final-submission-s25-t10-web-weaver
    * Description of test hardware: laptop, our costum PCBA, Sensors and actuators

## 1. Video Presentation

## 2. Project Summary

### Device Description

- Our device is designed to help freshman in kitchen, giving step by step instruction on cooking while prevent them from messing up. It is a modern state-of-art digital recipe box which have a fancy interface and sensitive monitoring system.

- Our project inspiration comes from our daily life. When I am a graduate student, I live outside the school and have to cool myself everyday. However, I nearly never cooked before so I messed up several times. And then I bought a recipe box from amazon.

  ![](A14G_inspiration.png)

  So we have that great idea. Would it be better if we can access to recipe for different steps of cooking more easily? And if there is a monitoring system, you will get alarmed before you notice you messed up. 

- We used Internet to build a online monitoring system so that you can access the sensor measurement  from other device such as your mobile phone. Meanwhile, we also made a online update system which can update the firmware image from cloud server so we don't have to flash to code locally every time we have some update.

### Device Functionality

- To design our device, we analyzed the users needs step by step. For a good recipe box, we need to give the user the ingredients need while cooking, and give our step by step instruction while cooking. To do this, we used a 7'' screen (which is larger than normal phone) to have a user friendly interface, we also have a joystick and button for user the switch between stages. To prevent user from messing up cooking, we build a monitoring system to measure the kitchen temperature and humidity as well as the food temperature while you are cooking. In that case, the user will get alarmed before the food is overcooked or the kitchen is filled with steam, so that there is still time for user to make it right.

- Our device have sensor to build a monitoring system.

  ​	SHT 45 temperature and humidity sensor

  ​	PT1000 RTD sensor

​	We also have actuator to build a user friendly interface.

​		7.0" 40-pin TFT Display

​	Besides, we have other critical component for user to operate.

​		Joystick

​		Button

- System-level block diagram

![](A14G_detailed_diagram.png)

### Challenges

We faced a lot of challenges in every stages of our design.

#### Hardware

1. We have a a problem in pin mapping. Because we almost use up all available pin in our MCU. To solve this, we tried several pinmux on Atmel start and finally figured out the available pin mapping.
2. In our PCB design, we have many component in our PCB while the PCB area is strictly  limited. To solve this, we have several rework to find out the tightest placement and routing.

#### Software

1. When developing SPI driver code for RA8875 LCD driver and MAX31865 Temperature sensor, we found that the official driver code is written in C++, to convert this to C and to be compatible with our Atmel Advance software framework, we analyzed the functionality of each function and rewrite it in C under ASF (advance software framework) to achieve the same functionality. Meanwhile, we use logic analyzer to analyze the official driver running in Arduino UNO as a golden protocol to debug  the code we wrote running in SAMW25 Xplain pro dev board.

#### Integration

1. In our Device integration, we notice that we made a mistake about cs pin in SPI Serial communication. To solve this, we reused other gpio pins as cs pins and use pull-up and pull-down as end and start of the transition.
2. One of the LED pin cannot be control by gpio, we think it is the manufacturer issue that connect that trace to 3.3V. We have no choice but to give it up.

#### Firmware

1.  When we are developing firmware for our project, we found that we cannot access SD card in other thread. To solve this, we use inter-thread communication to transfer request and respond between the UI task and the Wi-Fi task so that we can access files in SD card.

## 3. Hardware & Software Requirements

## 4. Project Photos & Screenshots

## Codebase

- A link to your final embedded C firmware codebases
- A link to your Node-RED dashboard code
- Links to any other software required for the functionality of your device

