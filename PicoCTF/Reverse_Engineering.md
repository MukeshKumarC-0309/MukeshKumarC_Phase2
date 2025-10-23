# 1.GDB Baby Step 1
Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.        

## Solution

The method i wanted to solve with this was pretty straightforward.I knew that the file i had was a binary file and i just had to disassemble to to get the required answers.Hence i found upon objdump which was a helpful command to help disassemble a binary file.Hence on doing so,I used the 'less' command along with it so that i can make viewing easier.Since it said that the number next to the eas part in main was the answer,i scrolled through the details and finally under the main section i was able to procure the number which i then converted to decimal with the help of google.     
        
<img width="1177" height="29" alt="image" src="https://github.com/user-attachments/assets/d7b58058-f425-4261-9979-3ab44755d32c" />       
       
<img width="970" height="899" alt="image" src="https://github.com/user-attachments/assets/7e0175c4-220d-4e09-8e7c-bb409bbc5423" />      
     
<img width="970" height="899" alt="image" src="https://github.com/user-attachments/assets/914daa53-0531-446d-9fb5-cf0997138830" />    
      
<img width="970" height="899" alt="image" src="https://github.com/user-attachments/assets/31145723-5aec-4f10-ac9e-ddce67dfa329" />        

'''   
bm_redlegend_5107@BMs-MacBook-Pro desktop % objdump -d ./debugger0_a | less      
./debugger0_a:  file format elf64-x86-64

Disassembly of section .init:

0000000000001000 <_init>:
    1000: f3 0f 1e fa                   endbr64
    1004: 48 83 ec 08                   subq    $0x8, %rsp
    1008: 48 8b 05 d9 2f 00 00          movq    0x2fd9(%rip), %rax      # 0x3fe8 <_GLOBAL_OFFSET_TABLE_+0x28>
    100f: 48 85 c0                      testq   %rax, %rax
    1012: 74 02                         je      0x1016 <_init+0x16>
    1014: ff d0                         callq   *%rax
    1016: 48 83 c4 08                   addq    $0x8, %rsp
    101a: c3                            retq

Disassembly of section .plt:

0000000000001020 <.plt>:
    1020: ff 35 a2 2f 00 00             pushq   0x2fa2(%rip)            # 0x3fc8 <_GLOBAL_OFFSET_TABLE_+0x8>
    1026: f2 ff 25 a3 2f 00 00          repne           jmpq    *0x2fa3(%rip)   # 0x3fd0 <_GLOBAL_OFFSET_TABLE_+0x10>
    102d: 0f 1f 00                      nopl    (%rax)

Disassembly of section .plt.got:

0000000000001030 <.plt.got>:
    1030: f3 0f 1e fa                   endbr64
    1034: f2 ff 25 bd 2f 00 00          repne           jmpq    *0x2fbd(%rip)   # 0x3ff8 <_GLOBAL_OFFSET_TABLE_+0x38>

0000000000001035 <__cxa_finalize@plt>:
    1035: ff 25 bd 2f 00 00             jmpq    *0x2fbd(%rip)           # 0x3ff8 <_GLOBAL_OFFSET_TABLE_+0x38>
    103b: 0f 1f 44 00 00                nopl    (%rax,%rax)

Disassembly of section .text:

0000000000001040 <_start>:
    1040: f3 0f 1e fa                   endbr64
    1044: 31 ed                         xorl    %ebp, %ebp
    1046: 49 89 d1                      movq    %rdx, %r9
    1049: 5e                            popq    %rsi
    104a: 48 89 e2                      movq    %rsp, %rdx
    104d: 48 83 e4 f0                   andq    $-0x10, %rsp
    1051: 50                            pushq   %rax
    1052: 54                            pushq   %rsp
    1053: 4c 8d 05 56 01 00 00          leaq    0x156(%rip), %r8        # 0x11b0 <__libc_csu_fini>
    105a: 48 8d 0d df 00 00 00          leaq    0xdf(%rip), %rcx        # 0x1140 <__libc_csu_init>
    1061: 48 8d 3d c1 00 00 00          leaq    0xc1(%rip), %rdi        # 0x1129 <main>
    1068: ff 15 72 2f 00 00             callq   *0x2f72(%rip)           # 0x3fe0 <_GLOBAL_OFFSET_TABLE_+0x20>
    106e: f4                            hlt
    106f: 90                            nop

0000000000001070 <deregister_tm_clones>:
    1070: 48 8d 3d 99 2f 00 00          leaq    0x2f99(%rip), %rdi      # 0x4010 <completed.8061>
    1077: 48 8d 05 92 2f 00 00          leaq    0x2f92(%rip), %rax      # 0x4010 <completed.8061>
    107e: 48 39 f8                      cmpq    %rdi, %rax
    1081: 74 15                         je      0x1098 <deregister_tm_clones+0x28>
    1083: 48 8b 05 4e 2f 00 00          movq    0x2f4e(%rip), %rax      # 0x3fd8 <_GLOBAL_OFFSET_TABLE_+0x18>
    108a: 48 85 c0                      testq   %rax, %rax
    108d: 74 09                         je      0x1098 <deregister_tm_clones+0x28>
    108f: ff e0                         jmpq    *%rax
    1091: 0f 1f 80 00 00 00 00          nopl    (%rax)
    1098: c3                            retq
    1099: 0f 1f 80 00 00 00 00          nopl    (%rax)
:
'''

## Flag
picoCTF{549698}

## Concepts Learnt
I learnt the use of the objdump command which can be used to disassemble a given binary file in this case the 'debugger0_a' file and the use of the less command which helps in viewing the output in an interactive mode.        

## Resources
https://www.google.com/search?q=How+to+disassemblea+binary+file+in+linux&oq=How+to+disassemblea+binary+file+in+linux&gs_lcrp=EgZjaHJvbWUyBggAEEUYOTIGCAEQLhhA0gEJMTk5MjRqMGoxqAIAsAIA&sourceid=chrome&ie=UTF-8         



# 2.ARMssembly 1
For what argument does this program print `win` with variables 83, 0 and 3? File: chall_1.S Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})             

## Solution
The file given is an assembly file which was orginally written in C.Hence we look through the file to find some code which prints you win.We find that under .LC0.Hence when we read the main block we find that the value must be 0 for it run 'you win'.Hence,we go through the global func which results in giving the final variable.We see that it’s just a sequence of storing,loading,basic mathematics formulae.ldr stands for loading certain data onto a stack and str means to store a data onto the stack.mov puts the value into the variable.lsl refers to left bitwise shift.sdiv stands for division and sub stands for subtraction.As we go through the steps one by one,we find ourselves in the stage 'sub' wherein 27-w0(at 12)(initial argument) should result in the final value which we want it to be 0.Hence the value that we want is 27 which when converted to hex is 1B.Hence to match the format we put it as '0000001b' which is the answer.str and load has the stack position as argument.       

<img width="1440" height="900" alt="image" src="https://github.com/user-attachments/assets/6fd60d95-41e1-4132-8327-161e6bf5a187" />      

<img width="1440" height="390" alt="image" src="https://github.com/user-attachments/assets/a677c56c-80ea-4351-b1ac-550d656bf239" />


## Flag
picoCTF{0000001b}         

## Concepts Learnt
I learnt how to read assembly files and what certain commands stands for and how they work such as mov,str,ldr,lsl and much more.It also helped me run through the code quickly to find the blocks of code which could actually help us.           



# 3.Vault Door 3
This vault uses for-loops and byte arrays. The source code for this vault is here: VaultDoor3.java     

## Solution

Here,when i downloaded the java file.I first tried to running it directly but to no avail as i did not have the vault passcode.Then when i read between the lines of code,i realised that there was a certain block of code which could give us the flag.Since i did not have much experience in java,i tried to recreate the same logic in python.When i wrote a new block of code in python for the same logic and run it with the same arguments,we successfully obscured the flag.   
     
<img width="686" height="780" alt="image" src="https://github.com/user-attachments/assets/9a47f985-dcc1-46f0-84b7-4235495da5bc" />      

<img width="686" height="780" alt="image" src="https://github.com/user-attachments/assets/3320460c-0339-46f2-91ae-cf7c06e735c9" />      

<img width="460" height="329" alt="image" src="https://github.com/user-attachments/assets/807d9155-46ea-475a-b0eb-d14486a104b0" />
     
<img width="1104" height="62" alt="image" src="https://github.com/user-attachments/assets/4192553c-eff9-44aa-a267-82bfe02f32d0" />     

'''
password = list("................................")
sample = "jU5t_a_sna_3lpm18gb41_u_4_mfr340"

for i in range(0, 8):
    password[i] = sample[i]

for i in range(8, 16):
    password[23-i] = sample[i]

for i in range(16, 32, 2):
    password[46-i] = sample[i]

for i in range(31, 16, -2):
    password[i] = sample[i]

flag = ''.join(password)
print(f"Flag: picoCTF{{{flag}}}")
'''    
   
## Concepts Learnt     
I learnt the concept of reading in between codes to find out the right part which can be executed to get the code.    
    
## Notes    
I had some initial trouble running the code as i tried to directly run the java code which kept asking for the password,which i didn’t have.    

