# How Do Computer Languages Work?

A computer can only execute machine code, a series of binary instructions made of 0s and 1s. Each instruction tells the processor to perform a small operation, such as adding two numbers, moving data in memory, or jumping to another instruction.

Programmers rarely write machine code by hand. Instead, we write code in _programming languages_, which are closer to English and mathematical notation and much easier for people to read and write.

Before a program can run, some tool must translate the code written in a programming language into machine code, the native language of the computer. Different languages perform that translation in different ways.


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

None of the examples above can run directly on the processor. Each must be translated into machine code first.

The main difference is when and how that translation happens. Some languages translate the entire program before it runs. Others translate it as it runs. Many modern languages combine both approaches. The next sections explain how each works. 

### Compiled languages

The most direct approach to that translation is a **compiled language**.

A program called a **compiler** reads the entire _source code_ once, checks it for errors, and then translates it into machine code. The result is usually an executable program or another machine-code file that the operating system can run.

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

Many widely used programming languages are compiled, such as C and C++, used mainly for operating systems, web browsers, databases, and game engines. Go is popular for cloud services, web servers, and networking software because it produces fast programs and makes concurrent programming easier. Rust is increasingly used for operating systems, browsers, and other systems software because it helps prevent many common memory-related bugs while maintaining high performance. Swift is Apple's primary language for developing apps for iPhone, iPad, and Mac.

### Interpreted languages

An interpreted language relies on a program called an _interpreter_ to run its source code. Instead of translating the entire source code into machine code beforehand, the interpreter reads the code and executes it as it goes.

It goes like this:

```
Source code
    ↓
Interpreter
    ↓
Program runs
```

Each time the program runs, the interpreter must translate the source code again. Because this work happens while the software is running, interpreted programs are often slower than fully compiled ones.

But the advantage of interpreted languages is that programmers can test changes immediately. They can edit the source code and run it again without waiting for a separate compilation step. This makes interpreted languages popular for automation, web development, data analysis, artificial intelligence, and rapid software development.

Python is the best-known example. Other widely used languages in this category include Ruby and PHP. Command-line languages such as PowerShell on Windows and Bash on Linux and macOS also execute scripts through an interpreter, but they are mainly used to automate operating system tasks.

This is the basic idea behind interpreted languages, but many modern implementations use additional techniques to improve performance. For example, some Python implementations first compile the source code into _bytecode_ before executing it. The next section explains what bytecode is and how this approach works.

### Languages that run on a virtual machine

Some programming languages combine ideas from both compiled and interpreted languages. Rather than compiling directly into machine code, they first compile the source code into bytecode.

Bytecode is a simpler set of instructions than machine code. Instead of running directly on the processor, it runs on a virtual machine. In the context of programming languages, a virtual machine is a program that provides an execution environment for bytecode.

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

The virtual machine reads the bytecode and translates it into machine code as the program runs. Many virtual machines use a technique called just-in-time (JIT) compilation, which converts frequently used parts of a program into native machine code just before they execute. This improves performance while keeping the flexibility of bytecode. 

**Java** was designed around this approach. Java programs compile into Java bytecode, which runs inside the Java Virtual Machine (JVM). **C#** uses a similar approach with the **.NET runtime**.

Because the virtual machine handles the final translation, the same bytecode can usually run on Windows, macOS, Linux, and many other operating systems without being rewritten.

### The lines are becoming blurred

The traditional distinction between compiled and interpreted languages is still useful, but modern programming languages often combine techniques from both approaches. As a result, the boundaries between these categories are no longer as clear as they once were.

But regardless of how a language is implemented, the destination is always the same.

Before the processor can execute a program, every instruction must eventually become machine code. Whether the translation is performed by a compiler, an interpreter, or a virtual machine, the processor ultimately executes the same binary instructions.