[BITS 16]
[ORG 0x7c00]
main:
mov ax,0x0000
mov ds,ax

mov si,string 
Call print
jmp$

print:
mov ah,0x0E
mov bh,0x00

.nextchar
lodsb
or al,al
jz .return
int 0x10
jmp .nextchar

.return
ret

string db '-------------(welcome to 41z_ OS)-------------',0
times 512-($-$$)db 0 