# Mikrodatateknik_HT2023 (Microdata Techonology Course)
- Laborations for Microdatatechnology, Spring 2023

# Description
- The repository highlights and archives my coursework, specially the laboratories.
- Each completed laboratory is showcased below with a video, clearly demonstrating the end result.
- All C code, laboratory description, lecture notes, etc are available in folders above. 

# Nucleo Board
- Type: STM32F411RE (datasheets and reference manuals are available in the repository)

# Lab0 - Blinky (intro)
- Displays a blinking LED on the STM32 Nucleo Board. For each time the lamp blinks, keep track of how many times it blinked so far and serially transmit that information through a print statement to PuTTY.

# Lab1 (Die roll)
- A die is rolled by clicking at the blue button located on the Nucleo Board. When the button is clicked, the die is rolled. When the button is released, the die result is displayed on the 7 green LED lamps (placed in a die looking structure) and then outputed on the 7-segment display.

https://github.com/mosmar99/Mikrodatateknik_HT2023/assets/47375043/1626080e-5c8b-4462-8e0a-5b816a750439

# Lab 2 (Traffic Lights)
- A traffic light simulator. Contains accurectly functioning traffic and pedestrian light LEDs. There's a button push for pedestrians to click on, if they do, an interrupt will be generated (which is handled by NVIC). To indicate a button push, a LED lamp turns on. The different states are implemented using a Mealy-Machine. The states and events are available in the lab2 folder. The internal ticks are utilized to set time intervalls for states.

https://github.com/mosmar99/Mikrodatateknik_HT2023/assets/47375043/9e80a8cc-e756-4568-ace0-6e7ff2ff6178

# Lab 3 (Clock & Button counter)
- The clock is implemented using one of the internal clocks, TIM1. It is set to generate an interrupt every half a second. A 24 hour clock is then implemented on a 4 segment display. The clock has two states HH:MM (hours:minutes) and MM:SS (hours:minutes). You can switch between which state you want to be displayed using a button. Upon clicking on the button an interrupt is generated.
- The button counter counts the amount of times you click on the button. However, it takes into account bounces. Often when one clicks on a button (if its a cheaper version), it takes some time until the button signal becomes stable. I measured the usual time it take for the button input signal to become stable using an oscilloscope. The button then only registers clicks which from its last flank has been stable for a constant amount of time (previously measured by the oscilloscope). Total button count is lastly displayed on the four segment display.

https://github.com/mosmar99/Mikrodatateknik_HT2023/assets/47375043/2d590cac-f38b-4def-85e2-374833d47b9e


