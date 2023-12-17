# WGMY2023

Splice 

Category: Misc

Description: Someone corrupted my QR code! Fortunately i got backup. Someone corrupted my backup!

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
