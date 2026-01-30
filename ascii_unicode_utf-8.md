# The Evolution of Character Sets and Character Encoding

An email from your friend in Czech Republic arrives your inbox. You open it and see
"????????????" as the subject line. What you just experienced is called encoding 
miss match. The phenomenon was to common back in the day that it has a name, "mojiback"


At its core, computer science is a system of representing digital information. 
computers  deal in numbers (more accurately, binary), not text. So representing 
numbers is straightforward. But for text, it's  a lot complicated. 

over the years a long list of encoding standards, ranging from overly simple to 
devilishly complex, have been created, by hardware manufacturers, by 
universities, by governments and  by corporations. 

as technology grew so also did the need to communcate accross continenetal borders. 
The need agree on a global standard for encoding text became painfully clear. 
ASCII was born in 1963 as the first attemtpt to create a unified encoding standard
for English letters. ASCII is 7-bit encoding standard that

Humans had to find a way to represent letters in computers. 

before standardization, digital communication used to be something of a wild wild 
west. Different manufacturers used different systems to encode letters.  

The history of character encodings is a history of humans trying to teach computers 
how to represent letters and language i digital form. 

## Terminologies: 

Character set
: mapping from character to number 

encoding
: A way to represent a number in a byte sequence for the purpose of decoding it 
later on



Character encodings was vendor-specific. Different hardware makers defined their 
own encoding standards. What is represented as 'A' in IBM PC-3000 might be 
'Z' in PDP-7 or, even worse, a non-printable character. Ig was sort of wild wild 
west

this confusion restricted digital communication to just two people with same computer hardware and configurations. 

## The Invention of ASCII

ASCII was invented in 1968 to solve the bottleneck of digital communication. ANSI, the american national standards institute, published ASCII as a standard for representing
letters in digital form in 1968. ASCII is an encoding system that maps letters 
to numbers using 7 bits. For example, the letter 'A' maps to ASCII code 97. Because 
ASCII uses 7 binary digits (0000000), it can store up to 127 unique characters (the maximum you can count to with). The later 'A', which is  97 in ASCII, would be 


uses 7-bits to 
represent up to 127 characters, including all alphabets, punctuation, and special characters in the English language. 

because ASCII only covers  the english language, various other people started 
device ASCII extensions to cater to characters  in other language not in English. 
This gave rise to character sets. And there were whole web pages full of this 
code. 

unicode has become the defacto standard for  character encoding. 

