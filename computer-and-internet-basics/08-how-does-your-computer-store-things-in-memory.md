# How Does Your Computer Store Things in Memory?

Everything stored on your computer (numbers, letters, photographs, songs, videos) eventually comes down to the same long sequence of **0s** and **1s**.

So how can the same two symbols represent so many different kinds of information?

The answer is that **bits have no meaning by themselves**. A pattern of bits means whatever everyone agrees it means. Sometimes those bits represent a number. Other times they represent a letter, a color in a photograph, part of a song, or an instruction for the processor to execute.

A _bit_ is the smallest unit of information a computer can store. It can have only two possible values: **0** or **1**. Since a single bit cannot represent very much, computers usually work with groups of eight bits. A group of eight bits is called a **byte**.

For example, this is one byte:

```
01100001
```

By itself, that pattern doesn't mean anything. Whether it represents the number 97, the letter **a**, part of a picture, or something else depends entirely on how the computer chooses to interpret it.

Let's start with numbers.

Computers store numbers using **binary**, a number system based on two digits instead of ten. In the decimal system that people use every day, each position represents a power of ten. In binary, each position represents a power of two.

For example:

```
Decimal:  13

Binary:   1101

          8 + 4 + 0 + 1 = 13
```

Because electronic circuits naturally have two stable states (on/off, high voltage/low voltage), binary is a practical way for computers to represent numbers.

A computer sets aside a fixed amount of space for each number it stores, so there is a largest value it can hold before it runs out of room. On a modern 64-bit computer, a whole number gets 64 bits of space, enough to count up to about 18.4 quintillion.

Computers also need to represent negative numbers. Modern processors almost universally use a method called _two's complement_. To turn a positive number into its negative counterpart, the processor flips every bit (changing every 0 to a 1 and every 1 to a 0) and then adds one. This technique  enables the processor to add, subtract, and compare positive and negative numbers using the exact same circuitry, without needing separate rules for each case.

Not every number is a whole number. Computers also need to represent fractions such as 3.14 or 0.5.

Most programming languages and processors store these values using floating-point numbers. Floating-point numbers work much like scientific notation. Instead of storing every digit directly, they store a set of meaningful digits, called the _significand_, and a scale factor that tells the computer where the decimal point belongs.

This system can represent an enormous range of values. The trade-off is that many decimal fractions cannot be represented exactly in binary. For example, the decimal number 0.1 has no exact binary representation, just as one-third cannot be written exactly using a finite number of decimal digits. Tiny rounding errors are therefore a normal part of floating-point arithmetic.

Numbers are only one kind of information.

How does a computer store text?

The simplest idea is to give every character a number. Instead of storing the letter **A**, the computer stores the number assigned to **A**. When the text is displayed, the operating system or application looks up that number and shows the correct character on the screen.

Early computers used a standard called **ASCII** (American Standard Code for Information Interchange). ASCII assigned numbers to 128 characters, including English letters, digits, punctuation marks, and common control characters such as `Enter` and `Tab`.

ASCII worked well for American English, but it could not represent most of the world's languages. It had no room for characters such as **é**, **Ж**, **中**, or **م**. And it certainly could not represent emoji.

The modern solution is **Unicode**.

Unicode assigns a unique number to nearly every character used in writing systems around the world, as well as mathematical symbols, currency symbols, punctuation marks, and thousands of emoji.

For example, all of these are Unicode characters:

```
A
Ж
中
م
😀
🚀
🎉
```


Unicode defines the characters themselves, not how they are stored in memory. That job belongs to **character encodings**.

The most common encoding today is **UTF-8**. UTF-8 stores familiar English text efficiently while also supporting every Unicode character. Because of that, it has become the standard encoding for websites, email, Linux, macOS, Android, and many modern programming languages and file formats.

At this point, you might wonder about photographs, music, and videos.

They work exactly the same way.

A JPEG image is simply a sequence of bytes interpreted according to the JPEG format. An MP3 file is a sequence of bytes interpreted according to the MP3 format. A video file is another sequence of bytes, organized according to yet another format. The bytes themselves are no different. Only the rules used to interpret them change.

This is one of the most important ideas in computing.

Computers do not understand numbers, letters, photographs, music, or emoji. They only store and manipulate patterns of bits. Everything else comes from the rules that programmers and standards organizations have agreed upon for interpreting those patterns.
