# Instrucciones_rtm32

Se encuentra disponible el Documento de Google por si se quiere apreciar mejor.
https://docs.google.com/document/d/1g78n8BffJCK6uq4r9ATktBEaJNMx5wPxH5_tD2Urzg4/edit?usp=sharing

**Instrucciones**

**LUI + ORI (para poder asignarles valores a los registros y probar las otras instrucciones)**

**LUI:**

opcode(L)=11001
rs = 00000
rt = 01011
h = 0
imm = 0000000000000001

Formato L:
opcode | rs | rt | h | imm

Sustituyendo este formato por sus valores binarios:
11001 00000 01011 0 0000000000000001

Pasando esto a Hexadecimal:
0xC8160001

Precondiciones:
Ninguna

Se muestran los comandos ingresados en consola y el resultado:
Ingresados:
Program Counter (PC) set to 0x00000008
RTM32> s [0x08] 0xC8160001
RTM32> n 1 
Stepped instructions. Target PC: 0x0000000C

Resultado:
...
DEBUG [src/debug/execution.m:17]: Stepping CPU pipeline for 1 cycles. Current PC: 0x00000008
TRACE [src/cpu.c:245]: RAM size: 0x00001000 read: 0x00000008
TRACE [src/cpu.c:466]: Instruction: 0xC8160001
TRACE [src/cpu.c:467]: Opcode: 0b11001
TRACE [src/cpu.c:479]: [LUI] R11 = 0x00010000
TRACE [src/debug/debug.c:295]: [5] Handler finished execution successfully

**ORI:**

opcode = 00101
rs = 01011
rt = 01011
h = 0
imm = 0000000011111111

Formato L:
opcode | rs | rt | h | imm

Sustituyendo este formato por sus valores binarios:
00101 01011 01011 0 0000000011111111

Pasando esto a Hexadecimal:
0x2AD600FF

Precondiciones:
Ninguna

Se muestran los comandos ingresados en consola y el resultado:

Ingresados:
TM32> s PC 0x10
Program Counter (PC) set to 0x00000010
RTM32> s [0x10] 0x2AD600FF
RTM32> n 1

Resultado:
…
DEBUG [src/debug/execution.m:17]: Stepping CPU pipeline for 1 cycles. Curr
ent PC: 0x00000010
TRACE [src/cpu.c:245]: RAM size: 0x00001000 read: 0x00000010
TRACE [src/cpu.c:466]: Instruction: 0x2AD600FF
TRACE [src/cpu.c:467]: Opcode: 0b00101
TRACE [src/opcodes/logical.m:6]: [ORI] R11 (0x000100FF) = R11 (0x000100FF)
| 0x00FF
TRACE [src/debug/debug.c:295]: [5] Handler finished execution successfully.




