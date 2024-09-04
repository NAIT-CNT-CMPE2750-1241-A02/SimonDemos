# Sample Project Proposal - RandoDie

**Abstract**

I intend to create a small (maybe portable) electronic die roller. The device will feature user-selectable die count and die face count. The dice rolls will qualify as NIST certified.

https://csrc.nist.gov/Presentations/2023/overview-of-nist-rng-standards-90a-90b-90c-22

**Hardware**

I have selected a *STM32G041* variant as the microcontroller as it is a cheap and simple(ish) MCU that contains a harware RNG. I have used a similar RNG in another MCU, so the transition should be possible. I have not used this particular MCU before.

The die or dice will be rolled based on accelerometer tap detect, so for this capacity, I intend to use the popular *ADXL343* accelerometer. I have used this accelerometer before, so I have library code that I can use (although it will require updating and feature addition).

The display to the user will be a standard 128x32 I2C OLED display. I have written libraries for the 1206 controller, so with modification, I should be able to leverage previous work here.

At least two buttons will included to permit settings changes by the user. These will require two GPIO pins, and may or may not use interrupts (probably not necessary).

This application qualifies for low power operation, so I may battery power the device, but research will be required to determine what kind of battery will be required. Initially, I was thinking of using a pair of CR2032 batteries, and an LDO regulator, but the OLED may require too much current. Research required. The other option is to power the device from USB, but that would limit the device use.

**Research**

Things I don't know, that I will need to do research on:
- MCU is new, so I will need to look into the programmer (probably the ST-LINK Mini V3).
- MCU might be compliant with the Segger J-Link programmer, and if so, I could possibly code this in Segger - this would be preferred!
- The accelerometer uses an interrupt line to indicate tap detect. Some research will be required to determine if interrupts or polling on the micro side will be required. Also, some experimentation will be required to determine the accelerometer settings to provide an ideal user experience.
- Power supply circuit will require research. It might be best to provide a LiPO battery with charge controller and automatic output. These setups are pretty cheap now, and certainly have the jam to run the device for weeks at a time. Some research into battery capacity and available outputs for a 3V3 setup is required. 

**Proof of Concept**

For my proof-of-life build, I will be using a development board that fits into a breadboard. [Actually, there is no development board for this device, so I'm cheating a little, and have pre-designed one. Students will be able to buy off-the-shelf development boards, or use a breadboardable MCU for their proof-of-life setup].

I will be using an existing carrier board (Sweet Sensor Suite R1.8) with the ADXL343 for testing purposes. The final PCB design will use a standalone device. 

**Stretch Goals**

If time permits (or motivation rises) I will include a USB bridge with VCOM port to offload roll history to the PC. Serious nerds will want to validate that the statistics of the die rolls are in line with expectations, so this would be a nice feature. 

One or two LEDs could be added to the design - not sure what purpose they would serve yet, but if there are unused pins on the MCU, why not?

Configuring the number of dice and the number of sides could also be done with the accelerometer, but would be more code. Buttons or motion... future me will need to decide.

Die profiles might enchance the user experience, so such quality of life features may be implemented if time permits. It's only more code, right?

**Final Build**

Ultimately I intend to design this around being in a 3D printed PLA case. Some consideration will need be made for the form factor of the case, where the buttons, LEDs, OLED Display, and USB conenctor will be. I fully intend to have my daughter design the case in TinkerCAD, as I don't have the skill or patience to design such a thing. Fortunately, we have a 3D printer at home, so that should facilitate getting this done, with iteration, pretty easily. 

The final PCB design will include all components, without carrier boards (with the excpetion of the battery and charge controller, if used), and should be quite small - well within the 10x10cm default board dimensions. Costs should be easy to control. The PCB will be designed to fit into the 3D printed case without stand-offs or screws. This will take some experimentation, and probably a few prints to get right. The case will be designed as two parts that sandwich the PCB. How the case will be fastened closed is a future-me problem.

**Schedule**

Week 1-2
- Finalize Design
- Procure proof-of-life components (MCU carrier, battery options)

Week 3-4
- Assemble proof-of-life components
- Master toolchain, begin software development

Week 5-6
- Finalize design, complete initial software design

Week 7-9
- Complete PCB design, software essentially complete
- Complete dimensions for case know, begin 3D case design around PCB dimensions

Week 10
- Send out PCB design for manufacture

When PCBs arrive
- assemble, program, and test with current software.
- complete added features, assemble into case

Check-off!



