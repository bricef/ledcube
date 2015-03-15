# Intro #
Instead of interrupting to draw, we could use the built-in interrupts to stop execution of the drawing method whenever there is activity on the USB. This would allow us to draw as fast as possible and not worry about the speed of upload.

# Ideas #


# NOTES (from ARDUINO/notes) #

#brice# Could we find a way to interrupt only when we are writing to the arduino using the USB cable?

#ed# so when were not USB'ing, we use the main loop?

#ed# We can set the interrupt to interrupt more often by changing the reset counter value, this would cause faster interrupts.


#brice# Is the USB cable on the TWI (Twin Wire Interface) or the SPI (Serial Peripheral interface)?

#ed#  from the datasheet: http://www.atmel.com/dyn/resources/prod_documents/doc2545.pdf

#ed#
> SPI Pins (MOSI, MISO,SCK,SS) are at: Port B Pins 3, 4, 5, 2
> TWI Pins (SDA, SCL) are at Port C pins 4 & 5.
> USB/Serial Pins (TXD, RXD) are at: Port D Pins 0 & 1.
> So no, the USB does not interfere with the SPI, or TWI interfaces.

#brice# The TWI comes with a handy interrupt that we could use. This would allow us to draw as quickly as possible.

#ed#  Nice, Im not sure how long it takes at the moment to write onto the shift registers, I guess you want to link them all in a long chain, and just push byes? Itd also save on the output pins.