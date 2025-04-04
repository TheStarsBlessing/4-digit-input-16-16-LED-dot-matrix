# 4-digit-input-16-16-LED-dot-matrix
This is a scanning LED display board that can drive a 16x16 LED array with a four-bit input signal at a frequency of 2 clock signals.
## Project Brief Introduction
This is a scanning LED display board that can drive a 16x16 LED array with a four-bit input signal at a frequency of 2 clock signals.

This simple LED dot matrix is a peripheral I made for my 4-bit CPU (that is, the famous TD4CPU) 
(4-bit CPU can only output 4bit data per instruction cycle, so the signals of the two instruction cycles need to
be combined to drive the '16*16' LED dot matrix), the circuit is simple, the board size is within '100*100 (mm)',
and a lot of beautiful pictures have been added, overall it is more beautiful.

This project has also been released on the Lichuang open source platform, please refer to the https://oshwhub.com/the_starts-blessing/4-bit-input-1616led-dot-matrix

## Project features
1. Admire the wives (crossed out) (too punishable), thank you Jia Li Chuang's color silk screen!
2. Integrate two four-bit data through internal registers, output to the '16*16' LED dot matrix after decoding, and any LED light on the dot matrix can be clicked every two instruction cycles.
3. Through the pin headers on the left and right sides, any row or column of LEDs can be directly operated.

## Project parameters
5V power input, 4-bit control signal input, input clock frequency not less than '48*(number of LEDs to be lit)'Hz, not higher than 10MHz (reference value).

## Principle Analysis (Hardware Description)
The clock signal is divided by a jk flip-flop (74hc112), Q and Q# are used as clock signals for 
the front-end and the back-end two 74hc161 (four-bit binary counters can be preset) respectively, 
and the front-end 74hc161 latches the input first 4-bit data on the falling edge of the first clock cycle: 
on the falling edge of the second clock cycle, the 74hc161 on the input side reads and latches the front-end, 
and the 74hc161 on the output side latches the input signal. At this time, the back-end 74HC161 output 
signal is input to 74HC154 (4-16 line decoder) for decoding, and finally the input side is inverted through 
two 74HC540 inverting control columns, and the output side controls the row, and an LED is lit at (row/column).

The Proteus simulation is shown in the figure below:

![image](https://github.com/user-attachments/assets/735195a7-ac22-46fe-a42a-20a7deaf1bd9)

## Precautions
1. If the color silk screen is abnormally overlapped, please cut it and stick it to its original position, and it can be restored by rendering it again.
2. In principle, commercial use is prohibited in this project, but commercial use is allowed after all color screen printing pictures are deleted. (According to the relevant regulations of Genshin Impact, products with official pictures are not available for commercial use, please refer to https://m.bilibili.com/opus/596519933203383519 for specific regulations)
## Reference diagram
Schematic
![image](https://github.com/user-attachments/assets/23c05919-b60d-4cb8-acab-0bb339ca4122)

Simulation diagram

![image](https://github.com/user-attachments/assets/93607fa6-1880-44a1-9f7d-a64ffa692d83)
![image](https://github.com/user-attachments/assets/3eabc957-451e-42ca-87de-0a001bb9da79)

## Physical drawing

![df0a0603b7d04e6f968344df1b82a6c8](https://github.com/user-attachments/assets/e6b4840c-002c-47d5-a21c-71110de96d46)
![微信图片_20250403235254](https://github.com/user-attachments/assets/30cd263e-884e-4946-a881-92ecdb2a41e3)

Tested in combination with TD4

![微信图片_20250404000537](https://github.com/user-attachments/assets/78bde76b-c7c9-4288-8ff3-8ffa084b59ef)

## Version updates
2024.11.18  Adjusted some of the silk screens
  
2025.4.3 The circuit diagram was re-uploaded
  
In the future, I will write a window program that can visually program this light board, so stay tuned!
