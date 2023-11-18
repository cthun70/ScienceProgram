# ScienceProgram
As part of company CSR project will be inviting some kids to do some science project. This time to expose them to AI and also how to train AI to do simple task. PicoVoice on STM32 seems to fit this purpose.

Feasibility Study to Port PicoVoice to a low Cost easily available board STM32F411CEU6 Black Pill 

https://stm32-base.org/boards/STM32F411CEU6-WeAct-Black-Pill-V2.0.html

https://stm32-base.org/assets/img/boards/STM32F411CEU6_WeAct_Black_Pill_V2.0-2.jpg

![image](https://github.com/cthun70/ScienceProgram/assets/13252483/72b67992-7c11-45f7-98fe-6e653ffa99bd)


First Preliminary Check, Flash/RAM/CPU should be compatible with PicoVoice STM32F411VE Discovery Demoboard.
****![image](https://github.com/cthun70/ScienceProgram/assets/13252483/a942d6fa-923e-49ed-8c52-a1d154d99071)

Proof of prototpye (Done & Working) -> Some notes taken...
1. Clone PicoVoice from github - https://github.com/Picovoice/picovoice
2. Create PicoVoice Account and get the Access Key and replace in "${ACCESS_KEY}" of the main.c
3. Build Picovoice stm32f411e-disco Demo project and flash to stm32f411ce.
4. Results is not working.
5. Debug using SWO doesn't work on stm32f411ce. Hack code to redirect debug log to UART
6. Log Shows Picovoice init failed due to Rhino rhn file library is not expected.
7. Download the latest rhn file from PicoVoice AI trainer website under Rhino using the smart lighting template. Solve the PicoVoice Init.
8. Result is still not working. Fail the detect WakeUp "PicoVoice" phrase.
9. PDM CLK is ok but the PDM Data is connected to PC3 which doesn't exists in stm32f411ce.
10. Hack the code to use PB15 on the stm32f411ce got it to work.
11. First prototype hack was successful.

Hardware (PDM Microphone ripped off from a USB Camera module)

![image](https://github.com/cthun70/ScienceProgram/assets/13252483/e2e06cd9-2b41-403f-b6b3-a6120f4cfea5)

Things To do....

1. Setup ST32CubeIDE Development Tool
2. Remove the stm32f411e-disco BSP and replace with STM32Cube Auto Generate.
3. More test to come later.....
