
# Fossils in Modern Computing Software

Modern computing feels a lot more abstracted and clean. We open a terminal, type commands, and send data over the network to someone across the Mediterranean. We rarely
think about the technology that sits beneath those functionalities. 

But much of today's software is layered upon tools that no longer exist. And traces of those tools still show up in device names and commands of modern software. I call them 
"fossils". This article is about some identifiable fossils in modern computing. 

Early computers were huge and expensive, having only one CPU despite filling up entire rooms. Because of the sheer size and prohibitiveness of these machines, computers were not personal devices. Individuals  didn't "own" computers. Universities and Corporations did. What people owned then were terminals. 

A terminals used to be physical machine/setup that included just a keyboard and a 
screen (or even a printer) connected to a computer sitting somewhere in a university basement. No CPU. No programs running locally. You type in characters, send them over wire; the big computer processes them, and sends back results as characters, and your terminal displays them on the screen. The terminal didn't do any "compute". It just sent keystrokes and displayed characters. 


Multiple terminals and their users could be connected to one central computer with a single CPU. And these users sometimes need to access the computer at the same time. 
To make this work, the computer is programmed to give each user a tiny slice of CPU time, switching rapidly between users to perform their tasks. This process became known as "timesharing". 

Today, even low-end laptops have multiple CPU cores, with far more compute than 
those giant IBM mainframes that filled entire rooms. Every user has their own 
machine, so no need for timesharing anymore. And what is shipped as a "terminal" in 
modern computers is actually a "terminal emulator", which is a software
program that ***runs on your computer***, drawing text on the screen using bit-mapped displays. That software program talks to your local OS or a remote computer (usually via TCP/IP). 


So, while old terminals were physical machines (display screen + keyboard) 
connected to central mainframes, modern terminals are software programs installed on your local computer, pretending to behave like old an hardware terminal. Hence the name "terminal emulator". 

Before bit-mapped displays and TCP/IP, computers didn't talk to each other a lot. Old terminals used to 