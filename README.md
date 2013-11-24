autoocr
=======

This is a small Raspberry Pi project to perform some automated optical character recognition (OCR) 
on scanned documents. 
I have set it up in conjunction with my other project `autoscan` but since it is tecnically independent 
I maintain it in a separate repository.


Approach
--------

The basic objective is to perform OCR on `.tif` files and normalize the output of the recognition process such 
that efficient search can be applied later.
The simplest output format in this case could be `.txt`.

After some investigation on the Web for OSS OCR software and some test I`ve come across the following nice blog 
from Andreas Gohr which provided some guidance on the selection process:

* http://www.splitbrain.org/blog/2010-06/15-linux_ocr_software_comparison

I decided to start with the `tesseract` OCR software to perform the actual recognition process. 
Tesseract can be found at code.google.com:

* http://code.google.com/p/tesseract-ocr/


Installation
------------

The best installation description I found is available here:

* http://ubuntuforums.org/showthread.php?t=1647350

It provides a detailed description on the installation of `tesseract` and the `leptonica` library which is needed to perform basic imaging operations:

* http://www.leptonica.org/download.html

Major installation steps are:

1. Install imaging libraries for development (can be done via `apt-get install`)
2. Install `leptonica` library version 1.69 (download and compile)
3. Install `tesseract` program version 3.02 (download and compile)
3. Install tesseract language sets for English and German

The installation blog above will guide you through all the steps 1-3. 
For the installation of the language packs I deviated from the description and did the following:

* Download the English and German language packs from http://code.google.com/p/tesseract-ocr/downloads/list.
* Extract and copy them to `/usr/share/tesseract/tessdata/`

This worked fine for me.

To check whether the installation is complete do the following:

    $ tesseract -v
    tesseract 3.02.02
	 leptonica-1.69
      libjpeg 8d : libpng 1.2.49 : libtiff 3.9.6 : zlib 1.2.7

This shows that leptonica is installed and the JPEG, PNG, and TIFF libraries are used. 
If your output deviates it is likely that your installation is not complete. 
In this case check back with the installation blog.






