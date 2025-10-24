# 2.Tunn3l_V1s10n
We found this file. Recover the flag.          

## Solution
We receive a file which has random gibberish when catted out.But on top it said 'BM' which could mean it’s a bitmap file.Hence i use exiftool to get more details and it's indeed a bitmap file but it is not opening which could indicate that the file is corrupted.Hence i open it in a hex editor and compare it with a working bmp file which indicates that the header was changed wantedly.Hence i change it and when i open it,i successfully get the image,but it shows a small image saying 'not a flag sorry'.Hence that was not the intended flag.But when examining the flag,it felt like it was cut out.So I had the idea of tampering with the size of the image.Also i analysed the way the sizes are mentioned.So i tampered with the length of the file changing to 800,which showed the flag.        

<img width="1242" height="465" alt="Screenshot 2025-10-24 at 9 02 04 PM" src="https://github.com/user-attachments/assets/2af0552b-6eb1-495c-8351-e82830e38b80" />       


![WhatsApp Image 2025-10-24 at 8 57 49 PM](https://github.com/user-attachments/assets/7c8281f0-1ebc-462a-bea3-9a49337754d4)        


![WhatsApp Image 2025-10-24 at 8 57 22 PM](https://github.com/user-attachments/assets/ad34fe37-b08f-4e0c-8cc3-b8ad8d2fd02f)         


![WhatsApp Image 2025-10-24 at 9 01 19 PM](https://github.com/user-attachments/assets/e7e2ce83-142a-424f-bbd8-6f58d52ffee6)        


![WhatsApp Image 2025-10-24 at 9 01 19 PM](https://github.com/user-attachments/assets/be76dfea-13f3-4172-a1af-1e695e57f89c)         


## Flag
picoCTF{qu1t3_a_v13w_2020}        
    
## Concepts Learnt
I learnt about a new kind of file ie.BitMap File and how we can mess around with the details of the file to get the desired output.I learnt how to use a hex editor to change certain details of a file.       

## Resources Used
Neo,A hex editor                 
A sample bmp file which i sourced from the internet     
https://www.filesampleshub.com/format/image/bmp        






# 3.m00nwalk
Decode this message from the moon.          

## Solution
First we receive a audio file which seems to be unlike a music file.Hence when i looked for clues,it said 'how did the picutres send from moon to earth'.The answer is SSTV.Hence I figured out that the audio was a SSTV file and hence we need a tool which helps us convert a SSTV file into something readable/viewable like a photo.Hence we open up a random online convertor which reads the sstv audio file and converts into a readable image.        

<img width="917" height="362" alt="image" src="https://github.com/user-attachments/assets/d6fb4150-8a94-4f65-89dc-0a5dd9dfd54f" />      

<img width="1168" height="900" alt="image" src="https://github.com/user-attachments/assets/b0fe7b8c-70d5-4e99-87ad-93d92e03b4f7" />


## Flag
picoCTF{beep_boop_im_in_Space}     

## Concepts Learnt 
I learnt about a new form of audio file which is SSTV signals(Slow-Scan Television) which was used to send pictures from moon to the earth.I learnt to use the available tools on the internet which help convert signals to a viewable Picture.         

## Resources
https://sstv-decoder.mathieurenaud.fr/      
