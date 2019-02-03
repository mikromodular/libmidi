# libmidi

The goal of the libmidi project is to provide a high-quality MIDI
software implementation that is suitable for use on microcontrollers.

Initially, the PIC18 family of microcontrollers will be supported
using the Microchip (TM) XC8 compiler. A Makefile is provided for
that environment.

This library is ALPHA; it has not been thoroughly reviewed or
tested at this time.

## Building

    git clone https://github.com/mikromodular/libmidi
    cd libmidi
    make

This assumes that the Microchip XC8 compiler suite is installed on
your system. Installing this software is beyond the scope of this
README. Please see http://www.microchip.com/mplab/compilers for
more details.

## Priciples of Operation

The libmidi library employs a callback scheme in which the user
registers callback functions to handle only the events that they
are interested in. Events for which no handlers are registered will
be processed silently by the library.

The callback mechanism is "driven" by invocations of the
**midi_receive_byte()** function, which must be called once for
every single byte received from the UART that is configure to
read MIDI events.  All protocol state is managed by the library.

This design is flexible because it allows the programmer to use
it in a polling loop or in an interrupt handler. It should be
noted, however, that use within an interrupt handler has not been
tested at all, and the author is not yet familiar with this use
case. If you're interested in using this library from an
interrupt handler, please contact the author so that we can 
discuss incorporating any changes that might be necessary.

## API Lifecycle

The following list outlines the steps, in order, that the programmer
must take to use the library.

1. Call **midi_init()** to perform one-time initializaton of globals.
2. Call **midi_register_event_handler()** to register callbacks for
   events (note on, note off, etc.)
3. Call **midi_receive_byte()** once for every byte received on the
   UART device. Calling this function "drives" the event dispatch
   system and may result in callback invocation.

## Implementation Notes

* **Note On/Off** Some devices do not seem to send note off messages. Rather,
they send note on messages with a velocity of zero. Your application should
probably account for this by checking for this condition and delegating to
your note off handler.

## Current Status

This library is currently in ALPHA.

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
