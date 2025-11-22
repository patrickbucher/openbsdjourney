+++
date = '2025-11-22T09:35:26+01:00'
title = 'GTK 2 Font Sizes'
+++

I installed Leafpad, which is based on GTK 2, in order to try out some different fonts. Ironically, the application was rendered using a comically sized font.

The GTK 2 font can be adjusted in the config file `~/.gtkrc-2.0`:

    gtk-font-name = "DejaVu Sans 16px"

This only looks reasonable with a Pixel indication (i.e. using the `px` suffix). A blank indication, such as `"DejaVu Sans 16"` renders a comically large font.

Use the `gtk-demo` program to see the changes for a wide variety of widgets. (Unfortynately, the titles within the _Info_ sections still render comically large.)
