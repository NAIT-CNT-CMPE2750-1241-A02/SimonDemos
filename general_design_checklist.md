# General Design Checklist

These are generic things you should validate in your design. Always.

Is your name and sheet/PCB information on all of your design documents?

Do all of your devices that take/manage power have bypass caps, and are those caps as close as possible to the supply pins? In some cases, plane exclusions may need to be in place to limit noise.

If you are using a LDO regulator with an enable line, validate that the enable signal is tolerant of your input voltage. Many regulators are designed to work with USB, so they are not tolerant to over 6V. If you are using a 9V battery or something, this will be a problem!

Are all unused pins explicitly marked as no connect?

If you are using I2C, the SCL/SDA lines *must* have pull-ups (typically 10K Ohm). Note: some modules may have pull-ups already installed. Don't guess, be sure. I2C devices only have the capacity to pull the SCL/SDA signals low, so this is not optional.

If you are using I2C, have you exposed test points on the board for troubleshooting? You should.

If you have a spare USART/UART/SCI port on your micro, you should pin it out for troubleshooting putposes. Like the I2C bus troubleshooting pads, these don't need to be populated, but future you might be very thankful that you added a place to connect a probe, if need be.

Have you included your name, the date, and the name of the project clearly on the top or bottom silkscreen layer of your board?

Have you included mounting holes (if appropriate) in your design? These are typically NPTH, unless you have a specific reason to make the PTH.

Have you added up the total maximum current that all devices on the PCB *can* consume? You will need to ensure that you have sufficient current supply in your design. Heat may also be a concern for high-current components. Regulator and battery selection is driven by what you find here. Voltage is the minimum requirement to get into the club, current determines how well you can dance.

Diodes (LEDs) behave like a chunk of wire, with a voltage drop. They will eat whatever current you supply, so they need appropriately valued current limiting resistors. Factor in the forward voltage drop when you hit that with the Ohms law stick.

Have you validated that your footprint matches the datasheet? Being the right size does not mean that the pin assignments are correct. This is very true for BJTs, SOT-23 variants, and switches. Double check that the pin assignments in the datasheet match the pin assignments in the footprint. 

Have you clearly dropped text annotations in silkscreen on the board to assist in operation and assembly? Clearly marking pin 1 where it could be ambiguous is a big help. For header pins, label them for function. Look at this through the lens of "if I need to look at the PCB design or schematic to figure out where this signal is, or what pin this is" you don't have enough annotations on the SS layer.

Have you checked your layout/design in 3D space to ensure that you have left enough room for connectors, buttons, human interaction, etc... ?

Ensure that if you have placed a USB connector on the edge of your board that you have correctly lined up the 'board edge' with the exact placement of the USB connector. Also, and this has happened, ensure that the connector is facing the right direction. This is critical to correct operation, and these items can't usually be mounted (without cost) locally.

If you are making a 4-layer board, ensure that you have the two internal planes as solid fills, with GND typically on the 2nd copper layer. You may fill the upper and bottom layer with GND as well, but don't use this as GND for device power. Always punch any surface-mount components into the internal GND plane.
