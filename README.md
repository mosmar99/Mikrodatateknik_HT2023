# Course Purpose:
_"The purpose of the course is to introduce students to microcomputer technology and embedded systems through theoretical and practical elements."_

# Description
- The repository highlights and archives my coursework, specially the laboratories.
- Each completed laboratory is showcased below with a video, clearly demonstrating the end result.
- All C code, laboratory description, lecture notes, etc are available in folders above.

## The course includes the following components:
- Introduction to microcomputers (including single-chip computers) and the structure of different processor families
- Low-level programming in Assembler and C
- Interface with the external environment (peripheral devices and buses)
- Development tools, debugging, and methods
- Code analysis, security, code certification, standards

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

# Lab 4 (LCD display using I2C protocol)
Displayed accurately ticking clock on liquid crystal display (LCD: hd44780) with mountained I2C port (id: pcf8574). Used TIM2, a 32 bit timer in order to count a clock signal on microsecond level to achieve desired delay. Implemented several functions that directly manipulate internal DDRAM memory slots. Following functions were implemented:

- TextLCD_Clear (TextLCDType * hlcd)
- TextLCD_Home (TextLCDType * hlcd)
- TextLCD_SetDDRAMAdr(TextLCDType * hlcd, uint8_t adr)
- TextLCD_SetPos (TextLCDType * hlcd, int col, int row)
- TextLCD_PutChar (TextLCDType * hlcd, char c)
- TextLCD_PutStr (TextLCDType * hlcd, char * str)
- My_Delay(uint32_t mysec) (microsecond delay)

# Lab 5 (Analog Digital Convert - ADC)
- Set up an ADC for reading a single value.
- Configure an ADC to read multiple values in sequence.
- Arrange an ADC for using interrupts.
- Write code to adjust the values obtained from ADC readings.

- Implemented LM35 Temperature Sensor, MH sensor series of type flying fish (a sensor which reads light intensity in lux) and a Joystick. The joysticks relative X and Y position, the temperature in celcius and lightintensity is displayed on the LCD screen using I2C interface. 16 and 32 bit timers are utilized. When the ADC has finished sampling, an interrupt is generated. There are 4 interrupt channels IN0 (Joystick X coordinate), IN1 (Joystick Y coordinate), IN4 (light sensor input value) and IN8 (temperature). Scan Conversion mode was enabled in order to successivly read from each channel, IN0 to IN8. Continuous conversion mode was also enabled to restart ADC sampling from first element in queue, i.e. after IN8 is sampled by ADC, next element to be sampled from is IN0. The end result can be seen in the video below:

https://github.com/mosmar99/Mikrodatateknik_HT2023/assets/47375043/ae8e7073-3941-4ce3-b7fc-a02ba33c6d0f

Note that the outputed vector from the ADC is an 12 bit vector whose minimum value is 0 and maximum 4095. Thus one needs to format the ADC reading to the sensor in question. For example, joystick coordinate x and y were displayed as a number that could vary between -1.00 and +1.00 respectively. Here is visualization of the joystick coordinates:

  <img width="347" alt="Screenshot 2023-10-06 212842" src="https://github.com/mosmar99/Mikrodatateknik_HT2023/assets/47375043/4a21204e-b591-4352-b14a-5db32e056c2f">

# Lab 6 
Through 3 PWM Channels implemented 3_Clor rbg light. Each color has 8 bits, enabling 2^(24) color combinations. Colors are rotating through the use of rudimentary trigometry, sinusfunctions with offsets. Each color is implemented using its own PWM channel, sampling every 480 clockcycles. The timer TIM1 is to count with a frequency of 10kHz, i.e. an interrupt is generated 10000 times a second. When an interrupt is generated, then the RGB colors are updated. The end result is shown in the video below:

https://github.com/mosmar99/Mikrodatateknik_HT2023/assets/47375043/49b83724-0f40-4f96-98b7-38e1bdeed6d2


