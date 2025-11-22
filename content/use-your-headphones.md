+++
date = '2025-11-22T09:19:56+01:00'
title = 'Use Your Headphones'
+++

In order to use your headphones, plug them in via USB and thenn check for dmesg messages:

    $ dmesg | grep -E 'audio[0-9] at'

Most probably, they will appear as `audio1` in the above output, which indicates that they are available under device number 1. Change your output device accordingly:

    $ sndioctl server.device=1

Two switch devices automatically upon connection/disconnection of the USB device, run the following commands:

    # rcctl set sndiod flags -f rsnd/0 -F rsnd/1
    # rcctl restart sndiod

The `-f` flag adds a device to the output devices, `-F` removes it; see `sndiod(8)`.

I got this information from the [OpenBSD FAQ](https://www.openbsd.org/faq/faq13.html#default).
