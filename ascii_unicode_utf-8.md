# The Evolution of Character Encoding (Or, How Computers Learned to Speak Every Language)

Ever visited a website and saw "??????" or the famous question mark in 
diamond (���) where a name or emoji should be? Ever downloaded a .csv or .txt file 
and opened it in Excel, only to find JosÃ©, FranÃ§ois, and random � symbols 
everywhere?

What you experienced, my friend, is called "encoding  mismatch." It's what happens when a computer system tries to interpret text using the wrong encoding scheme. All sorts of gibberish appear in random places: weird combination of characters like `â€™` instead of an apostrophe, or a Chinese author's name appearing as æä»¶. Sometimes entire streams of text is mangled. 

The thing is, computers only deals in numbers. All the videos you watch and the cute 
little selfies you take are stored and processed as a stream of bytes, a.k.a., 0s and 1s in groups of eight (1 byte = eight 0s and 1s).

So how do you represent the letter 'A' or the character '中' in a machine that only understands 1s and 0s? The solution is what is  called  **character encoding**, a system that maps characters to numbers, then represents those numbers as bytes in a computer's memory. 

Don't get confused. A character is a single, symbolic unit used in writing. In the English language, for example, there are 26 Latin letters that can be written as lowercase and uppercase characters. Text is formed by arranging these characters to convey information. 

<a id="terminology-definition"></a>
For the character encoding system to work, people had to agree on two things: 
- *the set of characters available to work with* (**character set**)
- *which number should represent each character* (**character encoding**)

The formal document that defines these details is what is called a 
**character encoding standard** (or **encoding scheme**). 

Over  the years we have gone from chaotic vendor-specific encoding schemes to ASCII, then to competing regional standards, and finally to Unicode and UTF-8. 

The history of character encoding goes as far back as the dawn of computing. But this article will focus mainly on the evolution beginning from the birth of ASCII. Nevertheless, I will give a short intro to how things were before ASCII.


## Before standards, character encoding was something of a wild wild west
In the early days of computing, there was no universal way to represent text in digital form. Character encoding was quite rudimentary. Different hardware manufacturers implemented their own encoding schemes for their computer systems. IBM had  the Extended Binary Coded Decimal Interchange Code (EBCDIC). Digital Equipment Corporation (DEC) developed proprietary encodings for its early PDP machines widely used in universities. UNIVAC systems also employed their own six-bit character codes. And so on. 

As long as storing and processing information remained confined to a single type of 
machine, there was no need for everyone to agree upon a standard. 

Then came the internet, which dramatically expanded the volume and reach of information interchange. 
Computers were no longer isolated systems; they were now connected across universities, countries, and continents. Text had to travel between different machines built by different manufacturers in different regions of  the world. A universal character set was needed to allow the emerging global stream of information to flow from machine to machine without impediment. So the development of ASCII began.

## ASCII: the first real standard

The American Standards Association (now ANSI) published ASCII (the American Standard Code for Information Interchange) in 1963. It was the first serious attempt at a universal encoding standard. 

ASCII is a system of representing text by mapping English letters to specific numbers. For example, the capital letter `A` in ASCII is 65, while the small letter `a` is 97. ASCII encoded characters using 7-bits, which means it had room for 128 unique character codes. This was enough to represent uppercase and lowercase English letters; digits (0-9); punctuation marks; and even some unprintable characters, technically called "control codes", like space (32), line feed (10), delete (127), and bell (7).
Yep, 7 literally made your computer beep.  

ASCII worked well for English text. And since the de facto standard for the length of a "chunk" in the computer industry is 8-bits, ASCII fit comfortably with one bit to spare. That last bit was sometimes called "the high bit", typically set to zero. 

But ASCII only handled unaccented English letters. No Cyrillic (Б, Д), no Chinese characters (你, 好), no fancy accents (é, ñ, ü) ... nothing beyond the basic Latin alphabet. As the internet went global and became accessible to people from various linguistic backgrounds, the need for a more inclusive encoding system became painfully clear.

## The era of code pages/extended ASCII

Many hardware vendors said fuck it and started using the 8th bit to add more characters from other European languages. That extra bit gave room for 128 additional characters, bringing the total to 256. The problem is that everyone had different ideas about what those extra 128 slots should contain. 

For example, IBM created code pages, which defined additional encodings for special characters in languages like Spanish and German, and some symbols for English users. Code Page 437 was used in the US and included characters for drawing boxes and lines on screen. Code Page 850 was for Western Europe and included letters like `é`, `ñ`, and `ü`. Code Page 866 was for Cyrillic. Code Page 862 was for Hebrew. 

Microsoft also developed Windows-1252 (a.k.a. "WinLatin1"), which included extra printable characters in the 0x80 (128) to 0x9F (159) range, such as Euro sign (€), smart quotes (“”), and additional punctuation. It supported Western European languages like English, French, German, Spanish, Italian, Portuguese, Dutch, etc. 

Most 8-bit ASCII variants (loosely called “extended ASCII”) kept their first 128 code points (0 to 127 / 0x0 to 0x7A)  exactly the same as standard ASCII, but the code points from 128 to 255 (0x80 to 0xFF ) varied between encoding families and even between code pages within an encoding family. 

As you would have guessed, all sorts of confusion ensued. The byte 0x82 might be `é` on one system, `ג `(Hebrew letter Gimel) on another, or something else entirely on a third system. If you wrote a document on a US system and opened it on a Russian system, you'd get gibberish. Characters would be replaced with completely different symbols. The bytes were correct; the interpretation was wrong. 

Encoding mismatches were so common that there was a slang for it: *mojibake*. The code page system helped within regions like Western Europe but made international communication worse. You couldn't mix languages in the same document. And you had to somehow track which code page each file was using. 

## The Asian language problem

The thing is, 256 characters were still nowhere enough. European languages could squeeze their entire writing system into 8-bit encodings. But the ideographic languages of East Asia couldn't. For example, Japanese uses three writing systems: hiragana, katakana, and thousands of kanji characters. Chinese has about 10,000 "basic characters". No way to fit all that into 256 slots.

So up to the 1980s, nearly 20 years after ASCII was invented, there was still no
universal standard for encoding text. The basic problems of character encoding remained:
- incompatible encoding schemes
- not enough code space

## Unicode: one standard for everything

The Unicode Consortium started the Unicode project in 1987 with the goal of supporting all languages in human history, living or dead.  The organization included people from different countries, companies, an cultures whose mission was to capture digitally all forms of human language and also to ensure that smaller groups speaking some obscure, lesser-known languages are also represented and preserved digitally. 


Unicode's design was simple and straightforward: make one unified character set that includes every character from every writing system on the planet. Give each character a unique number, called a *Code Point*, and never reuse that number. 

The Unicode code points are written in hexadecimal notation, prefixed by "U+". The
capital letter `A`, for example, has the code point `U+0041`.  Small letter `é` (with acute accent) is `U+00E9`. The Chinese character `中` is `U+4E2D`. The Face with Open Mouth (😮) is  `U+1F62E`. And so on.

Unicode has room for over 1.1 million code points (`U+0000` to `U+10FFFF`). Currently about 155,000 characters have been defined, which includes all known language characters and nearly 4,000 emojis. Yet that's only like 14th percent of the available code space. Plenty of space for more. 

But Unicode is not an encoding scheme. It's a *character set* &mdash; a mapping  that simply says *"this character corresponds to this number/code point."* [see terminology definition↗](#terminology-definition). And computers don’t store raw numerals; they store bytes. So those Unicode code points would have to be serialized (converted into a sequence of bytes) before they can be stored and processed in computer memory.


## Unicode Transformation Formats (UTF-8, UTF-16, UTF-32)

Unicode itself defines three standards for serializing its numeric values for storage in memory. They are `UTF-8`, `UTF-16`, and `UTF-32`, each of them provide a different way to turn Unicode code points into byte sequence. The numbers (8, 16, 32) signifies how many bits each format uses to store characters.

**UTF-32** is the simplest format. Each character is stored in exactly 32 bits (4 bytes). The character `U+0041`, capital letter `A`, becomes `0x00000041`. Because each character has a fixed length, you can jump to any position in a string instantly. No complexity. The downside is memory usage. English text becomes four times larger than ASCII. The word “Hello” takes 20 bytes instead of 5. UTF-32 is currently used in niche areas like  programming language  runtime and compilers. 

**UTF-16** uses 2 bytes (16 bits) to store common characters and 4 bytes ( two 16-bit units called "surrogate pairs") to store less common characters. So it's a bit more space efficient that UTF-32, but ASCII text still doubles in size. Plus, UTF-16 introduced the concept of **variable length encoding**, which sort of takes away the simplicity and straightforwardness of UTF-32. Variable length encoding means different characters use different number of bytes. In the case of UTF-16, the number of bytes depend on how common the character is in everyday usage. Common characters like `b` → 2 bytes. Less common ones like 𝒜 → 4 bytes. UTF-16 is used internally by the Windows API, and also by Java and JavaScript engines for string representation. 

UTF-8 takes a different approach, which makes it the practical standard for text encoding today. 
It's a variable length encoding standard (like UTF-16) that uses between 1 and 4 bytes to encode 
characters. It embeds structural information directly into the bit patterns of those bytes.

You can jump into the middle of a UTF-8 byte stream and find the start of the next character. The bit patterns make it clear whether you're looking at a single-byte character or part of a multi-byte sequence. Here's how: 

The first byte of a UTF-8 character tells you how long the sequence is:

- If the first bit is 0 (`0xxxxxxx`) → single-byte character (ASCII range of 0 - 127).

- If it starts with 110 (`110xxxxx`) → start of a 2-byte sequence.

- If it starts with 1110 (`1110xxxx`) → start of a 3-byte sequence.

- If it starts with 11110 (`11110xxx`) → start of a 4-byte sequence.
  
Every continuation byte (the byte that follows the first) is always indicated by `10`. 

Consider the word `résumé`, for example. The letters `r`, `s`, `u`, `m` are ASCII (unaccented English alphabet), so each one is  encoded as a single byte starting with 0: 

```css
r → 01110010
s → 01110011
u → 01110101
m → 01101101
```
But `é` (`U+00E9`) is beyond the ASCII range so it takes two bytes: `é ` → `11000011 10101001`. The first byte starts with `110`, signaling the beginning of a 2-byte sequence. The second byte starts with `10`, signaling that it continues the previous character. So the UTF-8 byte sequence for “résumé” looks like this: 
```css
r        é               s        u        m        é
01110010 11000011 10101001 01110011 01110101 01101101 11000011 10101001
```
Notice the pattern. ASCII characters begin with `0`. Two-byte characters begin with `11`. Continuation bytes begin with `10`.

That pattern is the key.

Because continuation bytes always begin with `10`, and starting bytes never begin with `10`, you can always tell whether you are at the beginning of a character or in the middle of one. This critical feature of UTF-8 is called **self-synchronization**. You can jump into the middle of a UTF-8 byte stream and find the start of the next character. 

UTF-8 is also backward compatible with ASCII. The first 128 Unicode code points (`U+0000` to `U+007F`) use exactly the same byte values as ASCII. Any valid  ASCII file is also correct UTF-8. This compatibility made large-scale adoption of UTF-8 possible. Systems could switch to UTF-8 without breaking existing ASCII text. Old software expecting ASCII could read UTF-8 English text without modification.

Of the three standards, UTF-8 emerged as the winner, the gold medalist. As of 2026, 99% of all web pages are transmitted in UTF-8. It's the default for HTML5, JSON, and XML. Most programming languages and databases default to UTF-8. If you're working with text on the web or in modern software, you're almost certainly using UTF-8.

## Common Encoding Problems

Despite standardization and UTF-8 dominance, encoding bugs still happen here and there. The most common issue is an encoding mismatch, a situation where text encoded with one scheme is interpreted using another. A classic example is "café" displaying as "cafÃ©". The text was encoded as UTF-8 (the é character is stored and transmitted as the hex sequence `0xC3 0xA9`), but another program interpreted those bytes as if they were Latin-1 or Windows-1252 encoding scheme, where `0xC3` is `Ã` and `0xA9` is `©`.

Missing encoding declarations cause problems too. If an HTML file doesn't specify <meta charset="UTF-8"> and the HTTP headers don't declare the encoding, the browser has to guess. Sometimes it guesses wrong. But this rarely happens because all modern browsers default to UTF-8. 

---

Character encoding seems like an obscure technical detail until something breaks. Then it becomes obvious how fundamental it is.
Every piece of text you see on a computer (web pages, emails, text message, lines of code) depends on characters being  encoded and decoded properly. The fact that we can now send messages that mix English, Arabic, Chinese, emoji, and ancient Egyptian hieroglyphs, and everyone sees the same thing, required decades of work and evolution to achieve. We went from a fragmented world where different computers couldn't reliably exchange text to a unified system that handles practically every written language. Unicode and UTF-8 aren't perfect are the best practical solution we have for repenting language in computers.









