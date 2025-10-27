# 1.RSA Oracle
Can you abuse the oracle?
An attacker was able to intercept communications between a bank and a fintech company. They managed to get the message (ciphertext) and the password that was used to encrypt the message.
After some intensive reconassainance they found out that the bank has an oracle that was used to encrypt the password and can be found here nc titan.picoctf.net 53329. Decrypt the password and use it to decrypt the message. The oracle can decrypt anything except the password.

## Solution
So we have been a netcat connection which when established gives us an encryptor/decryptor.We can give an input depending on the option we choose and it converts it into hex and changes it accordingly.Hence we have no clue or way of finding out the individual values of public key etc.Hence we have to approach the problem from another vector.We know that a^b*c^b is ac^b.Hence we use that to our advantage here.hence we have to give the hex value as 2 such that 2^e*m^e=(2m)^e.control+B gives an hex value as 2 hence we do that and it gives us a ciphertext.Next we open up python and multiply both values(the one we got and password.enc) to get a new value.We copy that value and go back to the nc connection,choose decrypt and give in this value.We get a decrypted hex which we then divide by 2 with the help of an online hex calculator.Next we convert it into ascii using online tools.Then we open up an ssl connection and successfully give in the key which gives us the flag.

<img width="1440" height="99" alt="Screenshot 2025-10-27 at 6 25 42 PM" src="https://github.com/user-attachments/assets/3a431a1a-01af-482c-845d-961c0694b04c" />        

<img width="1440" height="100" alt="Screenshot 2025-10-27 at 6 26 18 PM" src="https://github.com/user-attachments/assets/8293bde4-15b1-4d02-b1af-aa9d2d37b9fc" />        

<img width="1440" height="110" alt="Screenshot 2025-10-27 at 6 25 58 PM" src="https://github.com/user-attachments/assets/1952be02-e0d9-4e4c-bc71-a488eb2fa3cf" />        

<img width="1440" height="472" alt="Screenshot 2025-10-27 at 6 28 04 PM" src="https://github.com/user-attachments/assets/ccd0a97b-9acc-4b30-8197-a30f13949f23" />          

<img width="1440" height="749" alt="Screenshot 2025-10-27 at 6 28 25 PM" src="https://github.com/user-attachments/assets/8df5ae84-4909-47a7-a319-e104e347a7aa" />          

<img width="1440" height="50" alt="Screenshot 2025-10-27 at 6 26 29 PM" src="https://github.com/user-attachments/assets/a902311d-dd64-4c47-87f2-ef75e6a46bd9" />          


## Flag
picoCTF{su((3ss_(r@ck1ng_r3@_24bcbc66}


## Concepts Learnt 
I learnt how to bypass modular mathematics to sometimes get the output we want.Also I learnt about how a netcat and ssl connection work.I learnt abt hex to ascii conversions.

## Resources Used
https://www.calculator.net/hex-calculator.html?number1=6468c4c6c4&c2op=%2F&number2=2&calctype=op&x=Calculate          
https://www.rapidtables.com/convert/number/hex-to-ascii.html          



# 2.Custom Encryption
Can you get sense of this code file and write the function that will decode the given encrypted file content.        
Find the encrypted file here flag_info and code file might be good to analyze and get the flag.        

## Solution
So,in this challenge we have been given two files,one with flag information and another python file which holds some certain program/algorithm which can be used for encryption.So,in a way we have to reverse the process to get the flag.So,instead of writing another program from scratch i decided to take the bits and pieces of the program that i need from the original program and reprogrammed it according to the goal.Then i created a loop to switch the ciphers back to the original decipher which is used as the plaintext.Then i meddle with the main program,the XOR program which can be used to find the ciphertext if the plain text and key is given.Hence i add an extra variable 'k' there that prints the key also just to view it.Then i run the program with 'picoCTF{' as the key as i thought that since it’s present in the flag it might be the clue or you know part of the clue.But it just printed some random output.But there was one part of the the ouput that intrigued me.Something like aedurtu.....         
This is because i remember seeing something similar to this in the main program under the __main__ variable,so that was my next guess as key.Fortunately,it was the right key and i managed to unlock the flag.            

<img width="957" height="593" alt="Screenshot 2025-10-27 at 8 38 59 PM" src="https://github.com/user-attachments/assets/b390feaa-6f1c-4e62-94c7-4d3d592c5ed0" />           

<img width="1090" height="130" alt="Screenshot 2025-10-27 at 8 39 29 PM" src="https://github.com/user-attachments/assets/08f452fc-77a4-4cec-93dd-6024c1e33d6c" />          

<img width="957" height="593" alt="Screenshot 2025-10-27 at 8 38 43 PM" src="https://github.com/user-attachments/assets/df9752b1-f046-4816-8a42-e4bdaf13a996" />          

<img width="1090" height="150" alt="Screenshot 2025-10-27 at 8 39 46 PM" src="https://github.com/user-attachments/assets/666dddf8-95d1-47e2-add1-2d2f8b01e0c4" />          

## Flag
picoCTF{custom_d2cr0pt6d_019c831c}            

## Concepts Learnt 
I learnt how to reverse a program to trace back the process that had already been completed with the given output and code structure as reference.           



# 3.miniRSA
Let's decrypt this: ciphertext? Something seems a bit small.

## Solution
So this just involves basic decryption according to the RSA algorithm.We have been given a text file which contains the ciphertext,the public key e and the public key value.So all we need to do is to decode the message according to the algorithm.Hence i look up for online decoders and found one.I substituted in the values and recovered the flag successfully.          

<img width="1440" height="152" alt="image" src="https://github.com/user-attachments/assets/4d44bba6-c915-4fa7-acc6-8598cdaf002a" />              


<img width="786" height="709" alt="Screenshot 2025-10-26 at 5 41 14 PM" src="https://github.com/user-attachments/assets/95229736-7076-41c5-9946-682d1d94258d" />        

## Flag
picoCTF{n33d_a_lArg3r_e_606ce004}            


## Concepts Learnt 
I learnt abt the RSA encryption method and how we can encrypt or decrypt messages with the help of public key.I also learnt the use of RSA decoders which can help decrypt messages.               


## Resources Used
https://www.dcode.fr/rsa-cipher          

