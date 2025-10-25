# 1.Trivial Flag Transfer Protocol
Figure out how they moved the flag.                            

## Solution
Here,We are given a pcapng file which contains some clue about the data.Hence we open the file in wireshark to inspect the network and we see that some files have been send through the tftp protocol.Hence we use the export files option and take the files from tftp.They include 3 bmp pictures,a debian package and 2 files named plan and instructions.txt.When I open instructions.txt.On opening them i found out that i had to use the ROT-13 decoder to get both the messages.Hence I got 'TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE OUR FLAG TRANSFER.FIGURE OUT AWAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN' and 'I USED THE PROGRAM AND HID IT WITH-DUEDILIGENCE.CHECK OUT THE PHOTOS'.Hence i assume that the debian package might have something to help us out with.Hence when i open it using an installer i found an exe file called steghide.Steghide is a steganography tool which can be used to find hidden text or details in images.So i load up the exe file in terminal give the necessary arguments such as 'extract','-sf',and checked all the files one at a time giving the passphrase as 'DUEDILIGENCE'.In the 3rd picture it found some text which was then sent to flag.txt.When opened it showed us the flag value.                                    

![WhatsApp Image 2025-10-24 at 9 18 17 PM](https://github.com/user-attachments/assets/af84d699-5801-4b07-8838-cf912a3d590a)         

<img width="757" height="33" alt="Screenshot 2025-10-25 at 6 37 38 PM" src="https://github.com/user-attachments/assets/84422ae7-9168-4c17-af90-251554f0f335" />      

<img width="429" height="33" alt="Screenshot 2025-10-25 at 6 37 06 PM" src="https://github.com/user-attachments/assets/ab685a50-65fc-49a8-bcd3-2a33dc80bd22" />         

<img width="1440" height="586" alt="Screenshot 2025-10-25 at 7 12 30 PM" src="https://github.com/user-attachments/assets/44f15516-a879-4a13-ac37-f753cdf056b1" />     

<img width="1440" height="586" alt="Screenshot 2025-10-25 at 7 12 24 PM" src="https://github.com/user-attachments/assets/3bd1328a-5b8c-4949-8211-6ffb4aeee559" />       

![WhatsApp Image 2025-10-25 at 6 22 40 PM](https://github.com/user-attachments/assets/86ca6c60-2d36-488f-ba40-db366850575d)        

![WhatsApp Image 2025-10-25 at 6 23 01 PM](https://github.com/user-attachments/assets/cb8e1283-78d6-46fa-b38f-d9d04c651674)                                    

## Concepts Learnt
I learnt to read the pcapng file with the help of wireshark that can help us analyse networks and export files according to the protocol they were sent with.I learnt how to deal with debian packages,use stenography tools to find hidden details in images in this case bmp files.                            

## Resources Used
https://cryptii.com/pipes/rot13-decoder                        



# 2.Tunn3l_V1s10n
We found this file. Recover the flag.          

## Solution
We receive a file which has random gibberish when catted out.But on top it said 'BM' which could mean it’s a bitmap file.Hence i use exiftool to get more details and it's indeed a bitmap file but it is not opening which could indicate that the file is corrupted.Hence i open it in a hex editor and compare it with a working bmp file which indicates that the header was changed wantedly.Hence i change it and when i open it,i successfully get the image,but it shows a small image saying 'not a flag sorry'.Hence that was not the intended flag.But when examining the flag,it felt like it was cut out.So I had the idea of tampering with the size of the image.Also i analysed the way the sizes are mentioned.So i tampered with the length of the file changing to 800,which showed the flag.        

<img width="1242" height="465" alt="Screenshot 2025-10-24 at 9 02 04 PM" src="https://github.com/user-attachments/assets/2af0552b-6eb1-495c-8351-e82830e38b80" />       


![WhatsApp Image 2025-10-24 at 8 57 49 PM](https://github.com/user-attachments/assets/7c8281f0-1ebc-462a-bea3-9a49337754d4)        


![WhatsApp Image 2025-10-24 at 8 57 22 PM](https://github.com/user-attachments/assets/ad34fe37-b08f-4e0c-8cc3-b8ad8d2fd02f)         


![WhatsApp Image 2025-10-24 at 9 01 19 PM](https://github.com/user-attachments/assets/e7e2ce83-142a-424f-bbd8-6f58d52ffee6)        


![WhatsApp Image 2025-10-24 at 9 02 35 PM](https://github.com/user-attachments/assets/6f2b2dfa-2100-4690-85e7-317fe71e8fe4)         
    
        


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
