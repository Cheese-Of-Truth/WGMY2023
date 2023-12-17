# WGMY2023

#Splice 
Category: Misc
description: Someone corrupted my QR code! Fortunately i got backup. Someone corrupted my backup!

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

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/8110dd53-cb35-4661-9c2a-f3976c4659af)

By importing the first corrupted QR code into the recovery tools and try to extract QR information from the tool list, we get a decoded string from the picture.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/154f9db6-9b8a-407b-8419-a893169d0ae2)

Put it into the cyberchef and decode from base 64, we get the first half of the flag

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/23523128-caa4-47eb-8055-bc21bcc2b2e7)

We tried to decode the second QR code using the same method but unfortunately, the decoded string were corrupted. 

Hence, I recover the second QR code by comparing it with page3.png and filling up the missing pixel line by line. The middle 8 lines from left to right were missing so we only need to recover that 8 lines. Firstly, i filled up the black pixels that exist in the middle 8 lines of the third QR code first as black colour indicates that both QR code has black pixel in that position. After recover all of the black pixel, it is time to recover grey pixel to the QR code. In this time, we need to compare the QR code with the 2 QR codes. When we found a grey pixel in the Third QR code, we need to check whether the first QR code has that pixel filled. If it is filled, then we no need to fill up in the second QR code else we fill it up. 

This is the QR code after recovery, some of the pixels in the middle cannot be recovered as the first and second QR code are missing lines are intercepted at there, but this is already enough.

![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/5e054180-3639-41b9-8205-2126ea572e7a)

By extracting this recovered QR code, we got another decoded string. 
![image](https://github.com/Cheese-Of-Truth/WGMY2023/assets/145131434/37170e98-c687-4d44-a1ad-f281df1451be)

Combined this second half with the first half and decode from base 64, we got the flag: wgmy{5d7bdea65472ca9e615fcbd0f90a3b49}

This is the way i can think of to solve the challenge. Although it is not hard but definetly very time consuming. There might be some other better solving method to solve it faster.
