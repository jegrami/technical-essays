# How Do Input Devices Work?

The most common input devices are still the keyboard and the mouse, even nowadays when we have devices that also take touch or voice. We'll focus on the keyboard first, since it is the simplest case, and the same explanation carries over to the mouse and everything else with only small differences.

A keyboard does a very simple job. Every time you press or release a key, it sends a tiny piece of data to the computer that says which key changed and whether it was pressed or released

That message is sent immediately. The keyboard does not wait for the computer to ask for it. This creates a problem. The CPU might be in the middle of something else entirely, running a completely unrelated part of a program. It has no idea a key was just pressed. 

To get the CPU's attention, the keyboard raises a _hardware interrupt_. An interrupt is a signal that tells the CPU something needs immediate attention. The CPU pauses its current task and starts the appropriate _interrupt handler_ (more on this in a bit). When the handler finishes, the CPU resumes the program it was running before it was interrupted.All these happen so quickly that you never even notice the pause. (Humans are slow; computers are incredibly fast!)

The CPU knows how to respond to an interrupt, but it does not know what a keypress is, or a mouse movement, or a network packet. That knowledge lives in the operating system. For each type of interrupt, the operating system provides a different interrupt handler. An interrupt handler is a small piece of code written to process one specific kind of interrupt.

When the keyboard interrupt handler runs, it reads the key that was pressed and stores it in a keyboard buffer, a small area of memory that temporarily holds keypresses. The key stays there until the operating system can safely pass it to the program that is currently receiving keyboard input (which could your Notepad, VS Code, Chrome, a game, etc).

Other input devices work the same way, even ones that seem nothing like a keyboard. A mouse move or click, a finger touching a screen, a trackpad swipe. Each one raises its own interrupt, and each has its own handler ready to catch it. A touchscreen interrupt handler has more to do than a keyboard's, since it needs to figure out where on the screen the touch happened and whether it moved, but the basic pattern is identical. Something happens, an interrupt fires, a handler catches the data and files it away until it's needed.

Phones and tablets add sensors that didn't exist on a '90s-era desktop. An accelerometer detects when you tilt the device. A gyroscope tracks rotation. A fingerprint sensor or face-recognition camera checks who is holding the device. Each of these generates interrupts too, just like a keypress does, and the operating system routes the data to whichever app or system feature is waiting for it, whether that's rotating your screen or unlocking your phone.

Not every interrupt is equally urgent. The operating system assigns different priorities to different kinds of interrupts and handles the most urgent ones first. A Wi-Fi adapter, for example, may be receiving a steady stream of data that must be processed quickly to avoid losing information. A keystroke, by contrast, can usually wait a few milliseconds without you noticing. The operating system uses these priorities to keep the computer responsive. Urgent work gets handled first, while less urgent events wait their turn.

This idea of interrupts, one device raising a signal and the operating system reacting to it, is decades old. It traces back to early Unix systems and the hardware designs of that era, where each device was assigned a numbered interrupt request (IRQ), so the operating system would know which handler to run when a signal came in. Modern computers still use interrupts at their core, though the hardware now manages far more of the coordination automatically, which is part of why device conflicts of that kind are rare today.

What all of this adds up to is a computer that can sit and do many things without constantly checking each input device to see if anything happened. It waits, and lets the devices tell it. 

So if a keystroke can interrupt a running program at any moment, how does a computer manage to run many programs at once? We discuss that next.