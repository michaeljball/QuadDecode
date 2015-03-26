# Teensy31_QuadDecode
Quadrature Decoder library for Teensy 3.1 

From user TLB on the Teensy Forum:
https://forum.pjrc.com/threads/26803-Hardware-Quadrature-Code-for-Teensy-3-x

 Hardware Quadrature Code for Teensy 3.x

    Attached is my code for utilizing the hardware quadrature decode for Teensy3.x. As others have noted, it is not straightforward. The marketing department must have decided the applications that utilized more than 64K encoder counts or were not at least piecewise uni-directional were a small part of the market.

    I designed the code to minimize interrupt latency requirements and interrupt overhead. The code could have been a bit more straightforward if I had used both compare channels, but I wanted to save one for an exact position latch on hardware trigger feature (coming later).

    There is the class QuadDecode<n> (it is templated to use either the FTM1 or FTM2 channel).
    * The routines that can be called are:

    * setup() - constructor order of execution is not guaranteed, this
    * is called to set everyting up at the appropriate time. It overwrites some registers setup in
    * teensy.c for the tone() library, so has to be called after that.

    * start() - starts the counter counting at zero

    * zeroFTM() - zeroes the counter

    * calcPosn() - gets the current position. Needs to add the current
    * counter position to the basePosn. Accurate to within
    * interrupt latency and processing delay.

    The programs attached are:

    QuadDecode.h, QuadDecode_def.h - the important ones. Code to utilize the hardware quadrature decode channels on Teensy3.x

    main.cpp - an example of use. As I mentioned, it is templated, and I did not Arduinofy it, so this shows how to use the templates.

    GenEncoder.h, GenEncoder.cpp - program that generates simulated encoder signals for debug and development.

    Have fun. Let me know of questions or comments.

    -TLB
