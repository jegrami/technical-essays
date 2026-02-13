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

Over  the years we have gone from chaotic vendor-specific

