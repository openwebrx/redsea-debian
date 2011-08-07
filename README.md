redsea
======
This program decodes [RDS](http://en.wikipedia.org/wiki/Radio_Data_System) data received through
a sound card.

Why does it work?
-----------------
On certain FM radios, the 57 kHz RDS subcarrier can also be faintly detected at 57 / 3 = 19 kHz,
which is well below the [Nyquist frequency](http://en.wikipedia.org/wiki/Nyquist_frequency) for
an ordinary sound card's [ADC](http://en.wikipedia.org/wiki/Analog-to-digital_converter). This
allows us to plug the radio into the computer's Line In and, using digital filters and other DSP
sorcery, extract the RDS data.

What is this sorcery?
---------------------
The upper [Sideband](http://en.wikipedia.org/wiki/Sideband) of the RDS signal is bandpassed and
[downconverted](http://en.wikipedia.org/wiki/Heterodyning#Up_and_down_converters) to baseband. A
local oscillator signal is generated at 1187.5 Hz and
[phase-locked](http://en.wikipedia.org/wiki/Phase-locked_loop) to the
[BPSK](http://en.wikipedia.org/wiki/Phase-shift_keying#Binary_phase-shift_keying_.28BPSK.29)
waveform. A similarly phase-locked local clock signal is then used to demodulate the binary data.

Where will it work?
-------------------
The program runs on Linux and uses sox/alsa to read from the sound card. The GUI is written in
Perl and uses GTK2, Encode and IO::Select. Line in must be set on Capture and capture gain should
be reasonably high with no clipping.

Does it work?
-------------
YMMV.

Licensing
---------

    Copyright (c) 2007-2011, windytan (OH2-250)
    
    Permission to use, copy, modify, and/or distribute this software for any
    purpose with or without fee is hereby granted, provided that the above
    copyright notice and this permission notice appear in all copies.
    
    THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
    WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
    MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
    ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
    WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
    ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
    OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
