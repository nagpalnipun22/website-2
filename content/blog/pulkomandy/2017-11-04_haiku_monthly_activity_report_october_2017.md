+++
type = "blog"
author = "PulkoMandy"
title = "Haiku monthly activity report - 10/2017"
date = "2017-11-04T20:26:14.000Z"
tags = []
+++

<p>Hey there! It's time for the monthly report!</p>

<p>This report covers hrev51465-hrev51517.</p>

<h3>Packages</h3>

<p>Not much changes on packages anymore since the plan is to switch to the new repos generated by the buildbots "real soon now" (but the repo is still missing some critical packages). However, some maintenance efforts are still done.</p>

<p>The "bc" command is now moved to a separate package instead of being part of Haiku.</p>
<p>Many packages were rebuilt and updated following ABI changes in BControlLook.</p>

<h3>User interface</h3>

<p>The "channel sliders" used for volume control in media preferences now use a native tooltip. They used a custom one designed before the introduction of BToolTip which didn't really work. Now you can see the current volume in the tooltip while dragging the slider.</p>

<p>Font management was tweaked for better behavior with the new Noto fonts. In particular, it now recognize "thin" fonts properly as B_LIGHT_FACE, which avoids mixing them up with the regular variant of the font. This makes it possible to use Noto Sans Mono as the monospace font in replacement for Noto Mono, which is deprecated.</p>

<p>BWindow::FindView now works also for hidden windows (for example when using it on offscreen bitmap-views).</p>

<p>BTabView does not force a keyboard focus when deleting a tab anymore.</p>

<p>BFilePanel will not self-destruct when the volume currently shown is unmounted. This did not work because the application is ncouraged to reuse the BFilePanel and would not notice it is gone. Instead BFilePanel will now go to the home directory when this happens.</p>

<p>The new DeskBar resize knob got its drawing glitches fixed.</p>

<p>Due to repeated complaints by at least one user, it is possible again to enable switching workspaces by hovering the replicant and using the mouse wheel.</p>

<h3>System calls and kernel</h3>

<p>The wait4 syscall now behaves as expected. The implementation available in Haiku until now was broken and would return bogus data to userland. This will help with the Swift port, as well as getting Boost variant of Jam to run under Haiku.</p>

<p>sysconf(_SC_OPEN_MAX) will behave as expected by POSIX now</p>

<p>A missing fault handler in the 64-bit kernel caused it to KDL where segfault-ing the faultly app would have been enough.</p>

<p>The posix_spawn call had a file descriptor leak.</p>

<h3>Package management tools</h3>

<p>HaikuDepot uses a new way to communicate with the HaikuDepot server, which allows the application to run more smoothly.</p>

<p>pkgman progress bar was replaced with a status display showing a little more information (such as the package actual size).</p>

<h3>Drivers</h3>

<p>The FTDI USB serial-port driver now works better with modern FTDI chips. Previously this driver only handled the old generation USB1 ones.</p>

<h3>Translators</h3>

<p>The WebP translator recognizes more type of WebP files. The format is quite flexible and can do many things (lossy, lossless, ...).</p>