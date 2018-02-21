# libmidi

The goal of the libmidi project is to provide a high-quality MIDI
software implementation that is suitable for use on microcontrollers.

Initially, the PIC18 family of microcontrollers will be supported
using the Microchip (TM) XC8 compiler. A Makefile is provided for
that environment.

This library is ALPHA; it has not been thoroughly reviewed or
tested at this time.

## Current Status

This library is currently in ALPHA.

## Building

    git clone https://github.com/mikromodular/libmidi
    cd libmidi
    make

This assumes that the Microchip XC8 compiler suite is installed on
your system. Installing this software is beyond the scope of this
README. Please see http://www.microchip.com/mplab/compilers for
more details.


## Testing

There are no unit tests at this time. Unit tests are planned; they will
likely be developed to compile and run locally on the development
system and will be executed as part of the continuous integration
process once a system has been chosen.

## Examples

A simple example of MIDI processing is forthcoming.

## Contact
Please see AUTHORS in the root of the repository for contact information.

## Dependencies

None

## Future Planned Development

* MIDI Transmission (Only receive is supported at this time.)
* Support for multiple MIDI ports (only one in and one out will be
  supported as part of the first official release.)
