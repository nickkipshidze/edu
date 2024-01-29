Steganography is all the techniques used to exchange secret messages without drawing attention. It is the science of hiding information.

Some of the old school methods to hide information are: invisible ink, null ciphers, microdots or the use of pinpricks, deliberate misspelling or slightly different font to mark certain words in messages and maps.

## Null cipher

It's a normal text written in the clear, but includes a hidden message. For example:

```
Fishing freshwater bends and saltwater coasts rewards anyone feeling stressed. Resourceful anglers usually find masterful leapers fun and admit swordfish rank overwhelming anyday.
```

If we take the third letter in each word, we get: `Send Lawyers, Guns and Money.`

## Modern steganography

Refers to hiding information in digital images, audio files or even video. There are many methods and tools to do that. Nevertheless, and to have double protection, secret message are first encrypted and then hidden using a steganography tool.

The steganographic process can be described with the following formula:

*cover medium* + *data to hide* + *stego key* = *stego medium*

> **Note**
>
> If no encryption is added, there is no need for a *stego key*. 

## Hiding messages in pictures

This is usually done by:

1. LSB (least significant bit) insertion
2. Masking & filtering
3. Algorithms & transformations

Using LSB is famous, so I will choose it to explain how data can be hidden in images.

LSB is always the last bit on the right-hand side of any binary number. Changing this bit causes the least possible effect to the original value.

In a 24-bit image, there are 3 bytes of data to represent RGB values for every pixel in that image. This implies that we can store/hide 3 bits in every pixel.

For example, if the image has the following bits:
```
10010101 00001101 11001001  
10010110 00001111 11001010  
10011111 00010000 11001011
```

To store 101101101. We replace the original LSBs like this:
```
10010101 00001100 11001001  
10010111 00001110 11001011  
10011111 00010000 11001011
```

To reveal the stored message, the LSBs are extracted alone from the *stego medium* and combined together.

## Hiding messages in audio files

Two know methods to store messages in audio files are: *Frequency Domain and Time Domain*.

In **frequency domain**, a message can be stored in practically unused frequencies of audio files. For instance, in a CD where the sample rate is 44.1 kHz, the highest frequency without aliasing is 22.05 kHz.

Now, because the average peak frequency that an adult can hear is approximately 18 kHz, this leaves 4 kHz of frequency that is "practically unused". This space can then be used to hide a message (a copyright message for example).

In **time domain**, a message can be stored in the LSBs, something similar to what we saw with images. To maintain CD quality, it is important to encode at 16 bits per sample at a rate of 44.1 kHz. However, we can also record at 8 bits per sample using high significant bits (first bits of your left-hand side) and save the other 4 LSBs to hide our message without making any perceptible change to the audio quality.

In a comparison between the two, detecting messages hidden with time domain is harder because it requires more resources.

## Watermarking

Whenever there is a topic about steganography now days, *digital watermarking* is also mentioned. It refers to embedding hidden messages as well, but not for the purpose of sending secret information. Instead, watermarking is usually used for the following:
1. Copyright protection: include ownership information
2. Copy protection: include instructions to stop data copying devices from making and distributing copies of the original.
3. Prove data authenticity
4. Tracking: If copies of a file are distributed illegally, the source can be revealed if the master copies had unique watermarks included.

## Steganalyses and countermeasures

Steganalyses aim to investigate suspected information to determine whether they include any sealed data and reveal the hidden message if it exists.

Any unusual patterns (visual or statistical) are usually analyzed to detect suspected information. Hence, any method can be useful, for instance, image editors and hex editors (e.g. HEX Workshop).

Some methods are designed and developed to detect and reveal information hidden by known steganography tools. There are also enhanced and powerful [digital forensic](notes/forensics/digital%20forensics) analysis tools such as StegAlyzerSS (steganography analyzer signature scanner) developed by the Steganography Analysis and Research Center.

## References  
  
Introduction to Steganography. [cited 2010 Jan 08]; Available from: http://www.infosyssec.com/infosyssec/Steganography/menu.htm  

Gary C. Kessler. Steganography: Hiding Data Within Data. 2001 [cited 2010 Jan 08]; Available from: http://www.garykessler.net/library/steganography.html  

Steganography in Signals. [cited 2010 Jan 09]; Available from: http://www.owlnet.rice.edu/~elec301/Projects01/smokey_steg/steg.html  

Steganography Analyzer Signature Scanner. [cited 2010 Jan 09]; Available from: http://www.sarc-wv.com/stegalyzerss.aspx