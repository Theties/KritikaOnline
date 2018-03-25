# KritikaOnline

{ Game   : KRITIKA_Client.exe
  Version: 
  Date   : 2017-10-18
  Author : nani

  This script does blah blah blah
}

[ENABLE]


aobscanmodule(INJECT1,KRITIKA_Client.exe,8A 81 28 0C 00 00) // should be unique
alloc(newmem,$1000)

label(code)
label(return)

newmem:

code:
mov [ecx+00000018],0b
  mov al,[ecx+00000C28]
  jmp return

INJECT1:
  jmp newmem
  nop
return:
registersymbol(INJECT1)

[DISABLE]

INJECT1:
  db 8A 81 28 0C 00 00

unregistersymbol(INJECT1)
dealloc(newmem)

{
// ORIGINAL CODE - INJECTION POINT: 008904E0 

"KRITIKA_Client.exe"+4904CA: 8B 50 6C              -  mov edx,[eax+6C]
"KRITIKA_Client.exe"+4904CD: 83 C7 2A              -  add edi,2A
"KRITIKA_Client.exe"+4904D0: 57                    -  push edi
"KRITIKA_Client.exe"+4904D1: 68 5C 81 C7 01        -  push KRITIKA_Client.exe+187815C
"KRITIKA_Client.exe"+4904D6: 8B CE                 -  mov ecx,esi
"KRITIKA_Client.exe"+4904D8: FF D2                 -  call edx
"KRITIKA_Client.exe"+4904DA: 5F                    -  pop edi
"KRITIKA_Client.exe"+4904DB: 5E                    -  pop esi
"KRITIKA_Client.exe"+4904DC: 5D                    -  pop ebp
"KRITIKA_Client.exe"+4904DD: C2 04 00              -  ret 0004
// ---------- INJECTING HERE ----------
"KRITIKA_Client.exe"+4904E0: 8A 81 28 0C 00 00     -  mov al,[ecx+00000C28]
// ---------- DONE INJECTING  ----------
"KRITIKA_Client.exe"+4904E6: C3                    -  ret 
"KRITIKA_Client.exe"+4904E7: CC                    -  int 3 
"KRITIKA_Client.exe"+4904E8: CC                    -  int 3 
"KRITIKA_Client.exe"+4904E9: CC                    -  int 3 
"KRITIKA_Client.exe"+4904EA: CC                    -  int 3 
"KRITIKA_Client.exe"+4904EB: CC                    -  int 3 
"KRITIKA_Client.exe"+4904EC: CC                    -  int 3 
"KRITIKA_Client.exe"+4904ED: CC                    -  int 3 
"KRITIKA_Client.exe"+4904EE: CC                    -  int 3 
"KRITIKA_Client.exe"+4904EF: CC                    -  int 3 
}﻿
