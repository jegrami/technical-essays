## On Image Formats 

When considering image formats, there are generally two things to note: compression type and color depths. 

There are broadly two types of compression. Lossy compression and lossless compression. 

lossy: In lossy compression, though the image can usually be compressed to very small size, its quality degrades as it is repeatedly saved and transmitted. So the image can be made very small but to the detriment of the quality. Image quality gets progressively worse. 

**lossless**: ln loseless compression, the image can be compressed to smaller size - though not as small as in lossy compression - while retaining its original quality. 

### color depths

Under this we have indexed vs direct color depths. 

#### Indexed color images: 
Images with indexed color uses a technique where the color isn't directly stored in the image pixels but in a separate piece of data called the color lookup table. This helps keep the image size small. But the implication with this technique is that it can store only a limited number of RGB colors, usually around 256 color variations (8-bits). 

#### Direct color images: 
can store many thousands of colors. 

#### type of images and the compression they support

**BMP Images** - loseless/indexed and direct but barely compresses. That's why BMP images result in very large image files. No one ever uses it. It's good for ... nothing, as far as I know. 
**GIF** - loseless/indexed only. Image compresses to very small sizes, much smaller than BMP. But because it's indexed, it can store only 256 RGB colors. Good for logos, line drawing. 
**JPEG** - lossy/direct. JPEG was designed to make detailed photographic images as small as possible. It does its compression by removing specific details in the image pixels that the human eye doesn't notice. Since its direct, it can store thousands of colors, making for higher resolution. But being lossy, saving the file over and over again results in quality loss over time. Good for photographs. 

**PNG** 
The PNG image format is further divided into two types: PNG-8 and PNG-24. 
**PNG-8** - This is the indexed version of png images, created to replace GIF. It's loseless but does not support animation like GIF does, and it lacks support for older browsers like IE8. Good for alpha transparency.  
**PNG-24** - loseless/direct. Though loseless, png-24 has better compression than BMP and can store thousand of colors, but it results in a much larger  file than GIF and JPEG. 

As you can see, there is no "best image format"; everything is about tradeoffs. Some formats trade of size for richer color depths and more durable quality. While others sacrifice durable quality for file size. As a developer or designer armed with this knowledge you can now choose with image formats based on which is suitable for your use case. 
