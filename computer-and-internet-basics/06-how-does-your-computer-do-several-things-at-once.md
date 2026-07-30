# How Does Your Computer Do Several Things at Once?

# How Does Your Computer Do Several Things at Once?

Your computer rarely sits idle. As I write this article in VS Code, I have 16 browser tabs open, a movie downloading, music playing in the background, Figma and Telegram running, and three terminal windows open. Those are just the programs I can see. Behind the scenes, the operating system is also running hundreds of system processes and services.

How is one computer able to do so many things at once?

The answer has two parts. First, modern computers have multiple CPU cores, so some work really does happen at the same time. Second, the operating system rapidly shares those CPU cores among many running processes.

A **CPU core** is an independent processing unit inside the processor. Each core can execute instructions on its own. Most modern computers and smartphones have several CPU cores. Four, eight, or even 16 cores are common.

Each core can work on a different process independently. One core might be decoding a video, another might be rendering a webpage, while others handle background tasks such as syncing files or checking for software updates.

This is called **parallel processing**. It allows several processes to run simultaneously.

Even so, multiple CPU cores do not explain everything.

As you may have noticed, your computer often has hundreds of running processes. Even a powerful computer has far more running processes than CPU cores. An eight-core processor can run only eight processes at any given instant. Every other process has to wait for its turn.

If you open Task Manager on Windows or Activity Monitor on macOS, you will probably see hundreds of active processes. Many belong to the operating system. Others belong to web browsers, messaging apps, device drivers, security software, and background services.

The operating system solves this problem with **multitasking**.

One of the operating system's most important jobs is deciding which process runs on each CPU core. It does this with a component called the **scheduler**.

The scheduler keeps track of every process that is ready to run. It gives a process a brief turn on a CPU core, then switches to another one, then another, and so on. These switches happen thousands of times each second.

Because the switching is so fast, programs appear to run continuously, even though they spend much of their time taking short turns on a CPU core.

On a computer with multiple CPU cores, this happens independently on each core. Several processes can be running in parallel while many others wait for their turn.

This approach works because most programs do not need the CPU all the time.

A web browser may be waiting for a website to send more data. A music player may be waiting for the next chunk of audio. A word processor may spend most of its time waiting for you to press a key.

While one process is waiting, the scheduler gives that CPU core to another process that is ready to work. This keeps the processor busy instead of letting it sit idle.

In practice, many programs spend more time waiting for data than waiting for CPU time. Reading data from storage or downloading it from the internet is usually much slower than executing instructions inside the processor. For most everyday programs, waiting for data, not waiting for the CPU, is what causes delays.

Sometimes, however, a device needs the processor's attention immediately.

Suppose you press a key on the keyboard or click the mouse. The hardware sends an **interrupt**, which is a signal that asks the processor to pause its current work and respond to an urgent event.

The operating system quickly runs a small piece of code called an **interrupt handler** to respond to that event. Once it has finished, the interrupted process usually continues where it left off.

An operating system that can run many processes by sharing CPU time is called a **multitasking operating system**.

Modern versions of Windows, macOS, Linux, Android, and iOS all support multitasking. They combine multiple CPU cores, fast scheduling, and interrupt handling to keep your computer responsive even while hundreds of processes are active.

The result is a computer that appears to do many things at once. Some of that work is genuinely happening in parallel on different CPU cores. The rest happens because the operating system switches between processes so quickly that you never notice the change.
