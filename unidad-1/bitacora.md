# Unidad 1

## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 

## Actividad 4 
@suma_acumulada
M=0

@1
D=A
@i
M=D

@6
D=A
@limite
M=D

(LOOP)

@suma_acumulada
D=M
@i
D=D+M
@suma_acumulada
M=D

@i
D=M+1
M=D

@limite
D=M
@i
D=D-M

@LOOP
D;JNE

@suma_acumulada
D=M
@12
M=D

@END
(END)
0;JMP

<img width="1479" height="856" alt="Captura de pantalla 2026-01-30 163010" src="https://github.com/user-attachments/assets/1c8cd8e6-9489-4e6b-8f42-ae247b0a14c4" />

##Actividad 5
1. Describir las tres fases del ciclo Fetch-Decode-Execute ¿Qué rol juega el PC en el ciclo?

Fetch es el proceso en el que una instrucción guardada en memoria se traslada al Program Counter (PC) 
Decode es el proceso de decodificación o traducción de las intrucciones dadas a lenguaje de maquina, que es binario 
Execute es el proceso de ejecución de las instucciones dadas en el programa y los resultados se guardan ya sea dentro de un registro interno o dentro de la memoria RAM

El PC es quien realiza las operaciones o instrucciones dadas

2. Diferencia fundamental entre una instrucción A(@...) y una intrucción C (D,M,A...) en Hack

Una intrucción A carga de manera inmediata un valor en el registro A para especificar una posición en memoria o un valor constante
Una instrucción C es para realizar operaciones lógicas o guardar valores en variables 

3. Función del registro D, A y ALU

D es una variable que funciona para guardar un valor dado
A permite cambiar de posición en memoria que a la vez es un valor que puede ser registrado en una variable o esn memoria.

----(Terminar)----
4. Como aplicar un salto condicional en Hack

Para saltar usualmente usamos JMP y mencionamos a que posición se desea saltar, para realizar un salto condicional tenemos otros comandos como JNE (Jump if Not Equal) que nos permite saltar a una posición si un valor no es igual a cierto valor de una variable o no es 0




Una instrucción C, funciona para hacer operaciones entre variables o valores dentro de la memoria del PC

6. Diferencia entre D=M y M=D

en D=M le asignamos el valor guardado en memoria a la variable D
en M=D guardamos el valor de la variable D en memoria 

7. Que se necesita para leer el teclado y pintar y pintar un pixel en pantalla

## Bitácora de reflexión





