+++
date = '2026-05-20T06:06:13+02:00'
title = 'Upgrade to 7.9'
+++

OpenBSD 7.9 was released yesterday. This is the first time, I'm using OpenBSD when a new version is released.

Upgrading is versy simple:

    # sysupgrade

I was running this while typing the first line of this post. After downloading the upgrades, the system automatically booted into upgrade mode. Fortunately, Vim was able to recover the first sentence.

After the upgrade, another reboot was needed, then the system was ready.

A new version of the base system also comes with new packages, which need to be upgraded, too:

    # pkg_add -u

This took roughly five minutes.

Typing two commands and waiting for roughly ten minutes gave me half a year of improved but still stable software. So far, everything works fine!

And here we are again:

    $ screenfetch -Np
                                            _   
                                           (_)  
                  |    .                        
              .   |L  /|   .          _         
          _ . |\ _| \--+._/| .       (_)        
         / ||\| Y J  )   / |/| ./               
        J  |)'( |        ` F`.'/        _       
      -<|  F         __     .-<        (_)      
        | /       .-'. `.  /-. L___             
        J \      <    \  | | O\|.-'  _          
      _J \  .-    \/ O | | \  |F    (_)         
     '-F  -<_.     \   .-'  `-' L__             
    __J  _   _.     >-'  )._.   |-'             
     `-|.'   /_.          \_|   F               
      /.-   .                _.<                
     /'    /.'             .'  `\               
      /L  /'   |/      _.-'-\                   
     /'J       ___.---'\|                       
       |\  .--' V  | `. `                       
       |/`. `-.     `._)                        
          / .-.\                                
          \ (  `\                               
           `.\                                  

     patrick@openbsd.home
     OS: OpenBSD 
     Kernel: 7.9 GENERIC.MP#449 amd64
     Uptime: 20m
     Packages: 274
     Shell: bash 5.3.9
     Resolution: 2560x2520
     WM: dwm
     GTK Theme: Adwaita [GTK3]
     Font: DejaVu Sans 16px
     Disk: 19.8G / 394.5G (5%)
     CPU: Intel Core i7-7500U
     GPU: Mesa Intel(R) HD Graphics 620 (KBL GT2)
     RAM: 207MiB / 16130MiB
