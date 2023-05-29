# STM32_binary_pokes

Datasheet - https://www.st.com/resource/en/datasheet/stm32f103c8.pdf

Now we will talk about looking and analyzing this binary file that was extracted from the STM32. It is the firmware that controls the device and is what turns the leds on and off. There may be a timer that steps through a loop or something going on. And the LED is on for a while probably half a second. Talking about code for a bit. So for code to be used on a device like this, it needs to be compiled from a high level language like c to a low level language like assembly. The stm32 will then interperet the assembly instructons and will go through them step by step. This is the binary code that was extracted from the STM32. It is low level instructions and data that the stm32 interperts and executes to make the led blink and other things. So we need a tool that can actually look at the data as the processor sees it. The tool I will demonstrate is called GHIDRA. It is a tool built by the NSA. I will go over the installation and the use of this tool. 

#Ghidra

Gotta be my favorite reverse engineering tool. So go to https://github.com/NationalSecurityAgency/ghidra/releases and download the most recent version. Unzip it and cd into the directory. Then run with ./ghidraRun. More than likely openjdk wont be installed. So download it from the site on ghidras git or here. https://adoptium.net/temurin/releases/ . After getting this, select the whole direcotry as the jdk folder. After that it should run properly. 

#Usage

So go to file, and create a project. The stm32 is an arm cortex 32-bit RISC archeticture from the datasheet. Now go to file, new project and choose a name and a path for it. Then click the Dragon. Ghidras power is now RELEASED. click file, import, and import the binary. Then choose the language as arm cortex 32 bit little endian. 
![Screenshot_2023-05-29_01-48-01](https://github.com/mediocrereverse/STM32_binary_pokes/assets/133725400/924bfafe-cbb6-4902-b31b-845ea4860ae8)

Now you should be able to see the actual instructions in assembly language. On the right you should see a decompiler view. It will provide you something that looks kinda like c or whatever the compiled language may look like. Or it may not. Sometimes it sucks. 

With this we can start to actually debug the code running on the STM32. 
