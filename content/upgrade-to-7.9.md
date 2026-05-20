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
