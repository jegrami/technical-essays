# Download YouTube Videos in the Highest Quality with Pytubefix and ffmpeg

*Author:* jegrami
*Date:* 2024-12-12

Pytubefix is a drop-in replacement for Pytube, the original Python library for downloading YouTube videos. So it's a 'fix' of the broken Pytube API, hence the name. There are two methods of downloading videos with Pytubefix: the progressive stream method and the adaptive stream method. Pytubefix's default download method is the progressive stream. It gives you the video and audio streams in one file, so downloading it is pretty straightforward:

