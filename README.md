# INTERFACING DAC WITH 8086 KIT AND GENERATING SAWTOOTH AND SQUARE WAVEFORMS

## AIM
To write an assembly language program in 8086 to generate Sawtooth and Square waveforms using DAC.

---

## APPARATUS REQUIRED

| S. No | Item              | Specification   | Quantity |
|-------|------------------|-----------------|----------|
| 1     | Microprocessor kit | 8086            | 1        |
| 2     | Power Supply      | +5 V DC, +12 V DC | 1      |
| 3     | DAC Interface board | -              | 1        |

---

## ALGORITHM

### Measurement of Analog Voltage
1. Send the digital value to DAC.  
2. Read the corresponding analog value at its output.  

### Waveform Generation

#### Square Waveform
1. Send low value (00) to the DAC.  
2. Introduce suitable delay.  
3. Send high value to DAC.  
4. Introduce delay.  
5. Repeat the above procedure.  

#### Sawtooth Waveform
1. Load low value (00) to accumulator.  
2. Send this value to DAC.  
3. Increment the accumulator.  
4. Repeat step (ii) and (iii) until accumulator value reaches FF.  
5. Repeat the above procedure from step 1.  

---

## PROGRAMS

# 8086 Assembly Programs – DAC Interfacing

## Program: Square Wave

| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1000            | MOV AL,00H  | Load 00H in Accumulator           |
| 1003            |  OUT 0C8H,AL | Send through output port         |
| 1005            |  CALL DELAY(1100)  | CALL PROGRAM TO 1100      |
| 1008            |  MOV AL,0FFH |   Load 00H in Accumulator       |
| 100A            |   OUT 0C8H,AL|  Send through output port       |
| 100D            |  CALL DELAY(1100) | CALL PROGRAM TO 1100       |


| Memory Location | Program     | Comments                          |
|-----------------|-------------|-----------------------------------|
| 1100            | MOV CX,0505  | Load 0505H in Accumulator           |
| 1103            |  DEC CX | Decrement CX        |
| 1105           |  JNZ 1104  | RPEAT UNTILL ZERO      |
| 1108            |   RET |   RETURN TO MAIN PROGRAM      |


# Program: Sawtooth wave

## Assembly Program

| Memory Location | Program Instruction   | Comments                        |
|-----------------|-----------------------|---------------------------------|
| 1000          | START: MOV AL,00H  | Load 00H in accumulator       |
| 1003          | LOOP : OUT 0C8H,AL | Send through output port        |
| 1005          | INC AL             | Increment contents of accumulator |
| 1007          | JNC LOOP           | Jump if no carry (continue loop) |
| 1009          | JMP START          | Go to starting location         |

---

## Tabulation

| Waveform  | Amplitude | Time period | 
|-----------|-----------|-------------|
| Sawtooth  | 8.08v          |   1.642ms          | 
| Square    | 9.60v          |     6.052ms        |
---
## Model Graph

SQUARE WAVE
<img width="1280" height="728" alt="image" src="https://github.com/user-attachments/assets/9b22ae56-fd3e-4656-ab0d-2c955d9e01eb" />

SINE WAVE
<img width="1280" height="678" alt="image" src="https://github.com/user-attachments/assets/3581e92a-c415-4d8c-b4f0-060aa5f5b932" />




## OUTPUT IMAGE OF DAC(SAWTOOTH WAVE FROM DSO AND SQUARE WAVE FROM DSO)
![WhatsApp Image 2025-11-06 at 19 43 45_1e970ea3](https://github.com/user-attachments/assets/d0108fa5-3ef3-4ce9-a407-1e7a7c7872e3)
![WhatsApp Image 2025-11-06 at 19 44 02_68daa2b0](https://github.com/user-attachments/assets/ec7b4a7e-9d00-48ba-a637-429f8872ffee)



## Result

Thus, the *DAC was interfaced with 8086* and different *waveforms* were successfully generated.
