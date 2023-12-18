# WGMY2023

## Challenge Name: Splice 

### Category: Misc

### Description: Someone corrupted my QR code! Fortunately i got backup. Someone corrupted my backup!

A qr.zip file were downloaded from the challenge.

After extracting, there are 3 images inside the folder, page1.png, page2.png, page3.png.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/63c9aa60-321f-4d42-8bbd-772066bd45f3)

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/7be5292c-d15f-411a-9794-5cbe9cfd34d8)

The QR code in page1.png have some missing lines from top to bottom.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/ffef4de5-c0a2-4dfa-a0a7-fc5a99575845)

The QR code in page2.png have some missing lines from left to right.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/4877aa4d-a4f5-48a4-9077-d419f143f72d)

The QR code in page3.png seems to be a fusion of both QR codes, with no missing lines. In this merged code, each black pixel indicates that both the first and second QR codes have a filled pixel in that position, while grey pixels suggest that one of the QR codes has filled pixel in that specific position.

By searching QR recovery tools online, we found a tools called QRazyBox

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/3ea3788c-6997-4830-9393-ac0a0f8e171b)

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/8110dd53-cb35-4661-9c2a-f3976c4659af)

After importing the first corrupted QR code into the recovery tools and attempting to extract QR information from the tool list, we successfully obtained a decoded string from the image.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/154f9db6-9b8a-407b-8419-a893169d0ae2)

Put it into the cyberchef and decode from base 64, we obtained the first half of the flag. However, when we attempted to decode the second QR code using the same method, the decoded string turned out to be corrupted. 

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/23523128-caa4-47eb-8055-bc21bcc2b2e7)

I recovered the second QR code by comparing it with page3.png and adding missing pixels to the central 8 lines. I filled in the black pixels first as it indicates that both QR codes were occupied in that position.  For the grey pixels, I checked if the first QR code had them filled; if not, I added them to the second QR code.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/9fff7e24-f4ce-430e-836c-f0e3bc25888d)

This is the QR code after recovery, some of the pixels in the middle cannot be recovered as the missing lines in first and second QR code are intercepted there, but this is already enough.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/5e054180-3639-41b9-8205-2126ea572e7a)

By extracting this recovered QR code, we got another decoded string. 

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/37170e98-c687-4d44-a1ad-f281df1451be)

Combined this second half with the first half and decode from base 64, we got the flag: wgmy{5d7bdea65472ca9e615fcbd0f90a3b49}

This is the way i can think of to solve the challenge. Although it is not hard but definetly very time consuming. There might be some other better solving method to solve it faster.


## Challenge Name: Compromised
### Category: Forensic

The challenge come with a zip file called evidence.zip

After extracting it, there are many folders inside that look like a copy of a computer. So, I import it into FTK Imager and analyze it.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/b09f909b-e9b4-4b9b-8781-5f2a78367b4a)

After analyzing all the folders, 2 suspicious files were discovered.

The first file is an image stored in the Desktop folder, named 'flag.png.'

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/2e947734-352c-47ae-90a9-d474676cc3ad)

The image cannot be opened directly, so I checked its header with a Hex Editor.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/061488fc-e819-45a5-92db-a74b9e4480ae)

The file signature '50 4B 03 04' corresponds to the signature of a zip file, so I changed the extension from 'png' to 'zip.'

There is a 'flag.txt' file inside the zip file; however, we need a password to access it.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/42f7415d-1936-409e-9100-e03033fc53cf)

I tried to brute force the password with some tools but failed.

So i went to the FTK imager to find the password.

The second suspicious file is a binary file stored in 'AppData/Microsoft/TerminalServerClient/Cache' named 'Cache0000.bin,' with a size of 35,565 bytes. 

Additionally, in FTK Imager, we can observe that the file signature is 'RDP8bmp.'

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/ec2c83b3-b637-44f8-99fe-0d86a47d9990)


We searched on Google and found a published Python script called BMC-Tools on GitHub. This script can be used to convert the file into BMP images.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/a8ef9a94-d1bc-40b5-9a98-403ae471984d)

Download the whole script folder with git clone and execute it using this command: python3 bmc-tools.py -s Cache0000.bin -b -d.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/df27d1d5-f3e9-4797-a9ee-b159cf7e8f36)

Note that this command will generate around 2265 BMP image files. The '-b' option is used to generate a collage image for all 2264 images.

By observing 'Cache0000.bin_collage.bmp,' we can see that in one of the snippets, there is a complete password.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/46f119f5-5194-4c7c-88dd-6e548c3cea3e)

The passowrd is WGMY_P4ssw0rd_N0t_V3ry_H4rd!!!

unlock the txt file using this password, we get the flag in flag.txt: wgmy{d1df8b8811dbe22f3dce67ef2998f21c}
