---
layout: project
type: project
image: img/arduino_thumbwar.png
title: "Arduino Thumb War"
date: 2026-09-17
published: true
labels:
  - Arduino
  - Embedded Systems
  - CircuitPython
  - Sensors
summary: "A two-player Arduino game that uses force-sensitive resistors to measure player input, detect target force ranges, and signal a winner using the RGB LED."
---

Arduino Thumb War is an embedded systems project I built using an Arduino Nano ESP32 and force-sensitive resistors (FSRs). The goal of the project was to learn how variable resistance sensors can be used to measure physical input and how those sensor readings can be processed in software. The final result was a two-player game where each player applies pressure to an FSR and tries to reach a randomly generated target force.

For this project, I built a voltage divider using an FSR and a 10k resistor so the Arduino could measure changes in resistance as the sensor was pressed. I used the analog readings to estimate the resistance of the FSR and then converted that resistance into an estimated force value. Since the relationship between force and resistance is not linear, I used a power-law model based on the sensor's datasheet calibration curve to get more accurate force estimates.

Because the sensor readings could change quickly and contain noise, I also implemented averaging to make the force measurements more stable. The program continuously compared each player's force reading to a target range and tracked how long the player stayed within that range. Instead of allowing an instant win, a player had to hold the correct force for a set amount of time. When Player 1 won, the Arduino's RGB LED turned red, and when Player 2 won, it turned blue. After displaying the winner, the game automatically reset with a new random target.

This project gave me more experience working with analog sensors, voltage dividers, sensor calibration, data filtering, and non-blocking code using `time.monotonic()`. It also helped me understand how raw sensor data can be converted into useful physical measurements and then used to control the behavior of an interactive embedded system.
