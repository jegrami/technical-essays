# What Happens When You Switch On a Computer?

When you press the power button on a computer, within a few seconds, that silent box of chips turns into a working desktop asking for your password. A lot happens in that gap. The machine has to wake its hardware up, run a series of checks, find and load an operating system, and get that operating system to the point where it can hand control over to you. 

This all happens in a handful of well-defined stages. The first half of that journey is almost identical no matter whether you're on Windows, macOS, or Linux. It's only in the second half that the three platforms really go their separate ways. Let's walk through the whole thing.

## Stage 1: Power Reaches the Hardware

The moment you hit the power button, electricity flows into the motherboard. The motherboard signals the power supply unit (PSU) to wake up and start feeding stable, correctly-converted power to every component: the CPU, RAM, GPU, fans, and storage drives. Nothing else can happen until this power is stable, because feeding a CPU flaky power is how data gets corrupted or chips get fried.

Once power is steady, the motherboard passes control to the firmware. Firmware is a small program built directly into a chip on the motherboard. It sits there permanently, separate from anything stored on your hard drive, and it's the very first code the CPU runs. The CPU is hard-wired to jump to a fixed, known memory address the instant it powers on, and that address always points into the firmware chip.

Older machines called this firmware the BIOS, short for Basic Input/Output System. Most computers built in the last fifteen years or so run a newer version called UEFI (unified extensible firmware interface) instead. UEFI boots faster than BIOS, can work with much larger drives, and adds a security check called Secure Boot (more on that in a bit). 

People still say "BIOS" out of habit even when their machine is actually running UEFI, so the term sticks around even though the original technology has mostly been replaced.

The firmware's first job is to run POST (Power-On Self-Test). POST checks that essential parts such as the CPU, the memory, the keyboard, and any other core input devices respond correctly. It also checks the RAM's capacity, which memory slots are filled, and how fast it can run, because the CPU is going to need somewhere to hold instructions very soon. Around this same time, the firmware sends a basic video signal to the graphics card to display something on the screen, maybe to show the user that the booting process is underway,  though no operating system has been loaded yet. This is where you'll usually see a manufacturer logo or a POST screen appear.

If POST turns up a serious problem, like memory that isn't responding or no CPU detected at all, the system stops here. You'll typically hear a series of beeps or see an error message, since there's no point continuing to load an operating system on hardware that has no CPU.

## Stage 2: The Firmware Finds Something to Boot

With the hardware components confirmed to be working, the firmware now needs to find an operating system (Windows, Mac, Linux) to hand off to. It doesn't know in advance where that operating system lives, so it goes through a list of available storage devices looking for a program called a bootloader. First, it checks the internal drive, then a USB stick, then a DVD drive, and sometimes a network connection. For each device on that list, the firmware asks: "Do you have bootable code on you?"

On older BIOS systems, a device counts as bootable if it has a valid Master Boot Record (MBR), a tiny program tucked into the very first memory block on the disk. On UEFI systems, the firmware instead looks for a properly formatted EFI System Partition containing recognized boot files.

The firmware checks each storage device in order and moves to the next one if nothing bootable is found there. If it reaches the end of the list without finding anything, you get the familiar "no bootable device found" message.

This is also where Secure Boot does its work on UEFI systems. Before trusting whatever boot files it finds, Secure Boot checks their digital signature to confirm nothing has been altered or infected by malware. If the check fails, the system halts and usually offers a repair or recovery option rather than loading code that isn't secure. Apple runs a similar check on its own hardware. Macs built around Apple Silicon chips or the older T2 security chip verify the startup software before continuing, and will drop into Recovery Mode if anything looks wrong.

## Stage 3: The Bootloader Takes Over

Once the firmware finds a trustworthy bootable device, it loads the bootloader program from that device and passes control to it. 

It's worth noting why this extra step exists rather than the firmware just loading the whole operating system directly.

Firmware exists to do the bare minimum needed to get things started. It was never built with the ability to understand modern filesystems. It can't even access enough disk space to load the operating system directly into memory. That's the job of the bootloader. The bootloader understands filesystems well enough to locate specific files, and if your machine has more than one operating system installed, it can present a menu so you can pick which one to start.

Many systems actually split this into two steps. A tiny first-stage loader, small enough to fit inside the MBR or a basic EFI boot file, does almost nothing except pull a more capable second-stage bootloader into memory. That second-stage loader is the one that actually locates the operating system kernel, checks for any updates or installations that were queued up from the last time you shut down, and applies them before moving on.

Which bootloader you have depends on your operating system. Windows uses the Windows Boot Manager (`bootmgr`). macOS relies on Apple's own EFI-based boot process. Linux most commonly uses GRUB2, though older systems sometimes used a program called `LILO`.

## Stage 4: The Kernel Wakes Up Key OS Components

The bootloader's main task is to find the kernel, which is the core of the operating system. The Kernel is the part of the operating system that never stops working as long as the computer is on. It sets the rules for how programs and hardware will communicate. 

So once the bootloader finds the kernel, it loads it into memory, and then hands of control of the hardware too it.

Everything up to this point has been generic, low-level firmware work. From here on, an actual operating system is in control.

A kernel that has just started doesn't yet know what hardware it's sitting on top of. So one of its first jobs is called _autoprobing_, where it checks I/O ports (special hardware communication addresses where device controllers like storage, USB, network adapters tend to sit and listen for commands) to figure out what's connected. The kernel isn't guessing randomly. It knows how to identify the various hardware components, and it uses that knowledge to load the correct driver for each device it finds.

There's a catch here worth explaining. The kernel usually needs disk drivers to reach the rest of the operating system's files, but those driver files themselves live on the disk. To get around this, the boot process loads a small temporary filesystem into memory alongside the kernel, called an initramfs on Linux. That temporary filesystem carries just enough drivers to mount the real, permanent filesystem. Once the real filesystem is available, the initramfs has done its job and gets discarded.

You rarely see any of this happen directly anymore. On old text-only consoles, all these hardware and driver messages scrolled down the screen as plain text while the system booted. Modern systems hide that behind a graphical splash screen, though on Linux you can often still switch to a text view of the raw boot log with a key combination like Ctrl+Alt+F2, and switch back with a different combination such as Ctrl+Alt+F1 or F7 depending on the distribution.

## Stage 5: The First Process Takes Charge

Once the real filesystem is mounted and the kernel has a working picture of its hardware, it starts the very first process that will run in `userspace`, traditionally given process ID 1 (PID 1). This process is the ancestor of every other process that will ever run on the system, and its job is to bring the rest of the operating system online.

On most Linux systems today, this process is **systemd**. Older systems used a simpler program called **init**, and some used a variant called `upstart`. On Windows, the equivalent early role belongs to the Session Manager (`smss.exe`). On macOS, it's handled by `launchd`. The names differ, but the purpose is the same: get everything else started in the right order.

This process generally works through a similar sequence of jobs regardless of platform:

It checks the disks first. Filesystems can end up in an inconsistent state after a crash or an unexpected power loss, so the system often runs a quick integrity check before relying on them.

It starts the core services next. This covers the low-level plumbing every other program depends on: the process manager, permission handling, hardware watchdogs, the display and audio subsystems, and time synchronization.

It starts daemons. A daemon is a program that runs quietly in the background and handles requests as they arrive, like a print spooler, a network manager, or a firewall service. Running one long-lived daemon to handle a stream of requests is simpler and safer than starting a fresh copy of a program for every single request.

It prepares the system for a login. On Linux this classically meant starting several copies of a program called `getty` to watch the keyboard and screen, creating the familiar set of virtual consoles, though today one of those consoles is almost always claimed immediately by the graphical display system instead.

Finally, it loads your personal startup items. Anything you've set to launch automatically (antivirus software, cloud sync tools, a chat app, a game launcher) starts around this point. Your network connection typically comes online here too.

Somewhere in this sequence the operating system also runs its own self-check, confirming that recent updates installed cleanly. If an update is still pending, the system may apply it now and restart on its own, which sends the whole process back to the beginning.

## Stage 6: The Login Screen Appears

The last piece to start is the display system, the software responsible for putting graphics, a cursor, and a login prompt on your screen. On Linux this has traditionally been the X server, or Wayland on newer systems, and it takes over the screen from whatever console was previously in control. A companion program called a display manager is what actually draws the graphical login box you type your password into. Windows and macOS have their own versions of this same idea, `winlogon.exe` on Windows and the macOS login window process on Mac.

Once you log in, a desktop environment or shell loads and the boot process is finished. The machine has gone from a powered-off collection of parts to a fully interactive computer, usually in well under a 30 seconds.


## A Note on Sleep vs. Shut Down

It's worth mentioning how this whole process connects to the two power options you use every day. Sleep keeps your open programs and current work sitting in RAM, using a trickle of power to keep that memory alive, so waking the machine back up skips almost this entire sequence. Shutting down clears RAM completely and cuts power to everything, so turning the machine back on means walking through the full process described above from the very start.

That's the full journey, guys, from a powerless box of parts to a logged-in desktop, packed into the few seconds between pressing the button and seeing your screen. 