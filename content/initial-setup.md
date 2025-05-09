+++
date = '2025-05-09T18:22:22+02:00'
title = 'Initial Setup'
+++

The setup worked quite smoothly yesterday. However, since the WiFi card on my laptop requires a non-free firmware, I had to sit in the lotus position for a while next to my router to connect it through the cable to my network. But after the setup, the missing firmwares were installed automatically to my surprise.

Another pleasant surprise: I was prompted for a passphrase in order to encrypt my disc. This was extremely simple, compared to what I had to go through on [Arch Linux](https://www.paedubucher.ch/articles/arch-linux-setup-with-disk-encryption/).

Unfortunately, the WiFi didn't work out of the box—at least not my main WiFi network at home. The guest network and hotspot provided by my smartphone did, however, so there must have been an issue with my passphrase that uses a lot of special characters. Having changed my passphrase today, WiFi works without any issue. I also got to learn `ifconfig(8)` in the process, which is a rather convenient tool compared to what I'm used to on Linux.

With the WiFi connection established, I was able to copy my SSH public key to my other laptop, from where I got it up to GitHub. This allows me to write future posts on my OpenBSD laptop. However, there's still an issue with some characters on the console. I don't know if the _Spleen_ font just does not support those characters, or if my encoding is misconfigured. More on that later…

I also got to know the `apm(4)` utility for power management. The battery on my seven year old laptop is still rather good: being 88% charged, it still has a life estimate of 318 minutes, i.e. more than five hours!

In order to shut down my laptop without rebooting it, I figured out the `halt -p` command. Both `halt` and `shutdown -h` will just reboot the system.

I again was pleasantly surprised when I closed and re-opened the lid: The laptop went automatically into hibernation mode—and came back out of it without any issues.

The system boot takes quite some time, because the services are not started in parallel, and there happens a lot during bootup, e.g. relinking of some libraries and programs for security reasons.

There's still a lot to do until I have a useful second laptop (mostly for writing and programming), but OpenBSD just feels right for me at the moment. It's all so simple, tidy, and rock-solid. I'll be reading a lot of manpages during the weekend…
