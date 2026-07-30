# How Do Computer Languages Work?

A computer can only execute machine code, a series of binary instructions made of 0s and 1s. Each instruction tells the processor to perform a small operation, such as adding two numbers, moving data in memory, or jumping to another instruction.

Programmers rarely write machine code by hand. Instead, we use _programming languages_, which are closer to English and math, and much easier for people to understand. Before a program can run, some tool must translate the code written in a programming language into machine code, the native  language of the computer. How that translation happens is what separates the main kinds of programming languages.

For example, these programs all display the same message:

Python:

```python
print("Hello, world!")
```

Javascript:

```javascript
console.log("Hello, world!");
```
C: 

```c
printf("Hello, world!\n");
```

None of the above code can run directly on the processor. Each must be translated into machine code first.

### Compiled languages

The most direct approach to that translation is a **compiled language**.

A program called a **compiler** reads the entire _source code_ once (i.e., code written in a particular programming language), checks it for errors, and then translates it into machine code. The result is usually an executable program or another machine-code file that the operating system can run.

This is how the sequence goes:
```
Source code   
    ↓
 Compiler
    ↓
Machine code
    ↓
Program runs
```

Once the program has been compiled, you can run it as many times as you want. The compiler is no longer involved unless you change the source code and compile it again.

Because the processor executes the translated machine code directly, compiled programs are usually very fast. They also give programmers close control over memory and hardware. This makes compiled languages a good choice for software where performance matters, such as operating systems, web browsers, video games, databases, and software inside cars, medical devices, and household appliances.

Many operating systems are written largely in **C** and **C++**. **Rust** is becoming popular for systems software because it helps prevent many common programming errors while maintaining the speed of C and C++. **Go** is widely used for servers and cloud software, while **Swift** is Apple's primary language for developing apps for iPhone, iPad, and Mac.

### Interpreted languages

An interpreted language takes a different approach.

Instead of translating the entire program before it runs, a program called an _interpreter_ reads the source code and executes it as the program runs.

It goes like this:

```
Source code
    ↓
Interpreter
    ↓
Program runs
```

This means the translation happens every time the program runs. Because of this extra work, interpreted programs are often slower than fully compiled programs.

But the advantage for interpreted languages is that programmers can test changes immediately. They can edit the source code and run it again without waiting for a separate compilation step. This makes interpreted languages popular for scripting, automation, data analysis, and rapid software development.

**Python** is the best-known example. System administration tools such as **PowerShell** on Windows and **Bash** on Linux and macOS also work this way.

In practice, modern interpreters are often more sophisticated than this simple picture. Many first translate the source code into an intermediate form before executing it.

### Languages that run on a virtual machine

Many modern languages combine ideas from both compilation and interpretation.

Instead of compiling directly into machine code, they first compile the source code into _bytecode_. Bytecode is a simpler set of instructions designed to run on a virtual machine. A virtual machine is a program that behaves like a computer running inside another computer.

It goes like this:
```
Source code
    ↓    
Compiler
    ↓
 Bytecode
    ↓
Virtual machine
    ↓
Machine code
    ↓
Program runs
```

The virtual machine reads the bytecode and translates it into machine code while the program is running. Many virtual machines use a technique called **just-in-time (JIT) compilation**, which converts frequently used parts of a program into native machine code just before they execute. This allows programs to run much faster than a simple interpreter while keeping the flexibility of bytecode.

**Java** was designed around this approach. Java programs compile into Java bytecode, which runs inside the Java Virtual Machine (JVM). **C#** uses a similar approach with the **.NET runtime**.

Because the virtual machine handles the final translation, the same bytecode can usually run on Windows, macOS, Linux, and many other operating systems without being rewritten.

### The lines are becoming blurred

The simple categories of compiled and interpreted languages are still useful, but modern software often combines several techniques.

For example, most Python implementations first compile source code into bytecode before executing it. Modern JavaScript engines also generate bytecode and use just-in-time compilation to speed up programs as they run.

Every major web browser includes a JavaScript engine. This allows websites to do much more than simply display text and images. Javascript enables websites to do stuff like check a form before you submit it, update part of a page without reloading everything, play games, and run complex web applications.

Some languages can also be compiled ahead of time, interpreted, or use just-in-time compilation, depending on the tools and settings a programmer chooses.

For this reason, programmers today think less about whether a language is "compiled" or "interpreted" and more about how its implementation executes code.

But whether a language is compiled, interpreted, or runs on a virtual machine, the destination is always the same.

Before the processor can execute a program, every instruction must eventually become machine code. The compiler, interpreter, or virtual machine is responsible for translating the programmer's code into the binary instructions that the computer understands.
