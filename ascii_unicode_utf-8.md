# The Evolution of Character Encoding (Or, How Computers Learned to Speak Every Language)

Ever visited a website and saw "??????" or the famous question mark in 
diamond (���) where a name or emoji should be? Ever downloaded a .csv or .txt file 
and opened it in Excel, only to find JosÃ©, FranÃ§ois, and random � symbols 
everywhere?

What you experienced, my friend, is called "encoding  mismatch." It's what happens when a computer system tries to interpret text using the wrong encoding scheme. All sorts of gibberish appear in random places: weird combination of characters like `â€™` instead of an apostrophe, or a Chinese author's name appearing as æä»¶. Sometimes entire streams of text is mangled. 

The thing is, computers only deals in numbers. All the videos you watch and the cute 
little selfies you take are stored and processed as a stream of bytes, a.k.a., 0s and 1s in groups of eight (1 byte = eight 0s and 1s).

So how do you represent the letter 'A' or the character '中' in a machine that only understands ones and zeros? The solution is what is  called  **character encoding**, a 
system that maps characters to numbers, then represents those numbers as bytes in 
the computer's memory. 

Don't get confused. A character is a single symbolic unit used in writing. In the English language, for example, there are 26 Latin letters that can be written as 
lowercase and uppercase characters. Text is formed by arranging these characters to
convey information. 

For the character encoding system to work, people had to agree on two things: 
- *the set of characters available to work with* (**character set**)
- *which number should represent each character* (**character encoding**)
The formal document that defines these details is what is called a 
**character encoding standard** (or **encoding scheme**). 

Over  the years we have gone from chaotic vendor-specific encoding schemes to ASCII, then to competing regional standards, and finally to Unicode and UTF-8. 

The history of character encoding goes as far back as the dawn of computing. But  
this article will focus mainly on the evolution beginning from the birth of ASCII. 
Nevertheless, I will give a short intro to how things were before ASCII.


## Before standards, character encoding was something of a wild wild west
In the early days of computing, there was no universal way to represent text in digital form. Character encoding was quite rudimentary. Different hardware manufacturers implemented their own encoding schemes for their computer systems. IBM had  the Extended Binary Coded Decimal Interchange Code (EBCDIC). Digital Equipment Corporation (DEC) developed proprietary encodings for its early PDP machines widely used in universities. UNIVAC systems also employed their own six-bit character codes. And so on. 

As long as storing and processing information remained confined to a single type of 
machine, there was no need for everyone to agree upon a standard. But then came the 
internet, which dramatically expanded the volume and reach of information interchange. 
Computers were no longer isolated systems; they were now connected across universities, countries, and continents. Text had to travel between different machines built by different manufacturers in different regions of  the world. A universal character set was needed to allow the emerging global stream of information to flow from machine to machine without impediment. So the development of ASCII began.

## ASCII: The First Real Standard

The American Standards Association (now ANSI) published ASCII (the American Standard Code for Information Interchange) in 1963. It was the first serious attempt at a universal encoding standard. 

ASCII is a system of representing text by mapping characters to alphabets 7-bit encoding system that maps characters 


"Space was 32, the letter “A” was 65, etc. This could conveniently be stored in 7 bits. Most computers in those days were using 8-bit bytes, so not only could you store every possible ASCII character, but you had a whole bit to spare, which, if you were wicked, you could use for your own devious purposes: the dim bulbs at WordStar actually turned on the high bit to indicate the last letter in a word, condemning WordStar to English text only. Codes below 32 were called unprintable and were used for cussing. Just kidding. They were used for control characters, like 7 which made your computer beep and 12 which caused the current page of paper to go flying out of the printer and a new one to be fed in."