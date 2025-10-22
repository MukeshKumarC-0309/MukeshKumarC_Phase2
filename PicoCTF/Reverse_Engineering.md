# GDB Baby Step 1
Can you figure out what is in the eax register at the end of the main function? Put your answer in the picoCTF flag format: picoCTF{n} where n is the contents of the eax register in the decimal number base. If the answer was 0x11 your flag would be picoCTF{17}.
Disassemble this.        

## Solution
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
