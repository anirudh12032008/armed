# Pixel ARM Assembly
This is my first ARM assembly program, it has currently 4 awesome pixel arts. It has 2 screen, the buffer screen and the pixel screen. the buffer screen is cleared and updated with each art and the pixel screen is used to visualize the art

I even added few delays with the help of a cool hack of using computations to create a delay.

It was really fun and pain to work with ARM assembly especially the pixel display part!!

## How to Run 
## Use the ARMLite simulator --- https://peterhigginson.co.uk/ARMlite/
( its designed to be used with ARMLite simulator so it can't be shipped in binary)
1. Open the ARMLite simulator in your browser
2. Copy the code from `myprog.txt` (or from below) or download the file
3. Paste it into the editor or click load to load the file
4. Click "Submit" to assemble and run

## Screenshot and videos
<img width="589" height="432" alt="4" src="https://github.com/user-attachments/assets/3fe92927-fefb-47b2-bee4-7827d4c41540" />
<img width="655" height="426" alt="3" src="https://github.com/user-attachments/assets/e6126488-fb7c-4941-a3ba-5655e6889c14" />

https://github.com/user-attachments/assets/ac012184-83db-410f-93ab-ef09e5cf2665

```
      MOV R11,#0xFF0000
      MOV R12,#.white
      MOV R1,#screen2
      ADD R3,R1,#12288
clr1:
      STR R12,[R1]
      ADD R1,R1,#4
      CMP R1,R3
      BLT clr1
      MOV R2,#screen2
      MOV R4,#0
      MOV R5,#0
rl1:
      MOV R9,R5
      MOV R6,#64
dr1:
      MOV R10, #63
      SUB R7, R10, R6
      CMP R6, R7
      BLT mdx1
      MOV R7, R6
mdx1:
      MOV R13, #47 
      SUB R8, R13, R5
      CMP R5, R8
      BLT mdy1
      MOV R8, R5
mdy1:
      CMP R7, R8
      BLT min_d1
      MOV R7, R8
min_d1:
      AND R8, R7, #1
      CMP R8,#0
      BEQ db1
      B dw1
db1:
      STR R11,[R2,R4]
      B dl1
dw1:
      STR R12,[R2,R4]
dl1:
      MOV R0,#10000 
dly1:
      SUB R0,R0,#1
      CMP R0,#0
      BNE dly1
      LDR R0,[R2,R4]
      MOV R1,#.PixelScreen
      STR R0,[R1,R4]
      ADD R4,R4,#4
      SUB R6,R6,#1
      CMP R6,#0
      BNE dr1
      MOV R5,R9
      ADD R5,R5,#1
      CMP R5,#48
      BLT rl1
      B art2
art2:
      MOV R11,#0x0000FF
      MOV R12,#.white
      MOV R1,#screen2
      ADD R3,R1,#12288
clr2:
      STR R12,[R1]
      ADD R1,R1,#4
      CMP R1,R3
      BLT clr2
      MOV R2,#screen2
      MOV R4,#0
      MOV R5,#0
rl2:
      MOV R9,R5
      MOV R6,#64
dr2:
      ADD R7,R5,R6
      AND R8,R7,#7
      CMP R8,#0
      BEQ db2
      B dw2
db2:
      STR R11,[R2,R4]
      B dl2
dw2:
      STR R12,[R2,R4]
dl2:
      MOV R0,#10000
dly2:
      SUB R0,R0,#1
      CMP R0,#0
      BNE dly2
      LDR R0,[R2,R4]
      MOV R1,#.PixelScreen
      STR R0,[R1,R4]
      ADD R4,R4,#4
      SUB R6,R6,#1
      CMP R6,#0
      BNE dr2
      MOV R5,R9
      ADD R5,R5,#1
      CMP R5,#48
      BLT rl2
      B art3
art3:
      MOV R11,#0xFF00FF
      MOV R12,#.white
      MOV R1,#screen2
      ADD R3,R1,#12288
clr3:
      STR R12,[R1]
      ADD R1,R1,#4
      CMP R1,R3
      BLT clr3
      MOV R2,#screen2
      MOV R4,#0
      MOV R5,#0
rl3:
      MOV R9,R5
      MOV R6,#64
      AND R7,R5,#1
      CMP R7,#0
      BEQ er3
or3:
      MOV R8,#0
      B dr3
er3:
      MOV R8,#1
dr3:
      CMP R8,#0
      BEQ db3
      STR R12,[R2,R4]
      MOV R8,#0
      B delay3
db3:
      STR R11,[R2,R4]
      MOV R8,#1
delay3:
      MOV R0,#10000
dl3:
      SUB R0,R0,#1
      CMP R0,#0
      BNE dl3
      LDR R0,[R2,R4]
      MOV R1,#.PixelScreen
      STR R0,[R1,R4]
      ADD R4,R4,#4
      SUB R6,R6,#1
      CMP R6,#0
      BNE dr3
      MOV R5,R9
      ADD R5,R5,#1
      CMP R5,#48
      BLT rl3
      B art4
      156
art4:
      MOV R11,#0x00FF00 
      MOV R12,#.white 
      MOV R1,#screen2
      ADD R3,R1,#12288
clr4:
      STR R12,[R1]
      ADD R1,R1,#4
      CMP R1,R3
      BLT clr4
      MOV R2,#screen2
      MOV R4,#0
      MOV R5,#0 
rl4:
      MOV R9,R5
      MOV R6,#64 
dr4:
      MOV R7,R5
      LSR R7,R7,#2 
      ADD R7,R7,R6 
      AND R8,R7,#7 
      CMP R8,#0
      BEQ db4
      B dw4
db4:
      STR R11,[R2,R4] 
      B dl4
dw4:
      STR R12,[R2,R4] 
dl4:
      MOV R0,#10000
dly4:
      SUB R0,R0,#1
      CMP R0,#0
      BNE dly4
      LDR R0,[R2,R4]
      MOV R1,#.PixelScreen
      STR R0,[R1,R4]
      ADD R4,R4,#4
      SUB R6,R6,#1
      CMP R6,#0
      BNE dr4
      MOV R5,R9
      ADD R5,R5,#1
      CMP R5,#48
      BLT rl4
      HALT
      .ALIGN 1024
screen2:.DATA
```
