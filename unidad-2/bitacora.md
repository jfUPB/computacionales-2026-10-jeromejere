# Unidad 2

## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 

##Actividad 1

<img width="491" height="258" alt="Captura de pantalla 2026-02-04 162712" src="https://github.com/user-attachments/assets/803b3b22-d543-4d5d-8e64-8c62e5a044db" />

##Actividad 2

<img width="1354" height="441" alt="Captura de pantalla 2026-02-04 163134" src="https://github.com/user-attachments/assets/959adc47-6c6f-455a-b78c-5a10cea6cacd" />

##Actividad 3

(START)

// i = SCREEN
@SCREEN
D=A
@i
M=D
//Inicio la pantalla pintando una linea
@SCREEN
M=-1

(LOOP)
@KBD 
D=M
@100
D=D-A
@derecha
D;JEQ

@KBD 
D=M
@105
D=D-A
@izquierda
D;JEQ
@LOOP
0;JMP


(derecha)
@i
A=M
M=0
A=A+1
M=-1
D=A
@i
M=D
@LOOP
0;JMP

(izquierda)
@i
A=M
M=0
A=A-1
M=-1
D=A
@i
M=D
@LOOP
0;JMP



@fin
(fin)
0;JMP

## Bitácora de reflexión



