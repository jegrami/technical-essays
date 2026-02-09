# The Evolution of Character Encoding (Or, How Computers Learned to Speak Every Language)

Ever visited a website and saw "??????" or the famous question mark in 
diamond (���) where a name or emoji should be? 

What you experienced is called "encoding  mismatch." It's what happens when a computer
system tries to interpret text using the wrong encoding scheme. All sorts of gibberish
appear in random places: weird combination of characters like `â€™` instead of an apostrophe or a Chinese author's name appearing as æä»¶. Sometimes entire streams of text is mangled. 

The thing is, computers only deals in numbers. All the videos you watch and the cute 
little selfies you take are stored and processed as a stream of bytes, a.k.a, 0s and 1s in groups of eight (1 byte = eight 0s and 1s).

So how do you represent the letter 'A' or the character '中' in a machine that only understands ones and zeros? The solution is what is  called  character encoding, a 
system that maps characters to numbers, then represents those numbers as bytes in 
a the computer's memory. Don't get confused. A character is 




