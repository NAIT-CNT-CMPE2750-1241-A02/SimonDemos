# Micro selection guide

***ATmega328***

If you don't need a super powerful micro, or any special features, I would suggest that you go with the ATmega328P and ATmega328PB micros for breadboard and PCB designs. This chip is well supported by the materials in BrightSpace, and has many library/code samples available.

J105 can sell these to you for ~$4.20, and the one and only programmer you need is ~$36.44, also available from J105. This programmer does **not** feature debug support, so it's a little tricky to write code with it.

***STM32***

If you are brave, or need a micro with a little more jam, you could go with a STM32 variant. You can purchase development boards for some of these chips, and the NUCLEO-G031K8 is an example of this:

https://www.digikey.ca/short/n2345z9r

These are very low cost development boards, with the debugger built in (you don't need any programmers at all at the breadboarding stage). Also, the device is programmed and powered from USB. Moving to a PCB for this device is more complex, and once you do, you will need a programmer. The STLINK-V3MINIE is the programmer you would use in the standard ST environment:

https://www.digikey.ca/short/zq3f09tf

As an alternative, you could also use a J-Link programmer with Segger - a very nice development environment:

https://www.segger.com/

Programmer:

https://www.segger.com/products/debug-probes/j-link/models/j-link-edu-mini/

This is not a cheap programmer ($~87), and we may end up having a few to loan out.

As referenced in my project proposal, there are other variants of these chips with different peripherals. The STM chip I'm using has a hardware RND in it, but there is no dev board.

# 2025 Update -> This has changed a little. See current documentation in the course.

