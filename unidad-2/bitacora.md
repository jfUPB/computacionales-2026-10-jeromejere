# Unidad 2

## Bitácora de proceso de aprendizaje


## Bitácora de aplicación 

## Actividad 1

<img width="491" height="258" alt="Captura de pantalla 2026-02-04 162712" src="https://github.com/user-attachments/assets/803b3b22-d543-4d5d-8e64-8c62e5a044db" />

## Actividad 2

<img width="1354" height="441" alt="Captura de pantalla 2026-02-04 163134" src="https://github.com/user-attachments/assets/959adc47-6c6f-455a-b78c-5a10cea6cacd" />

## Actividad 3

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

## Actividad 5

@10
D=A
@a
M=D

//Direccion de la variable 
// p = &a
@a  
D=A
@p
M=D

// *p =20 
@20
D=A

@p
A=M
M=D

##Parte 2

@10
D=A
@a
M=D

@5
D=A
@b
M=D

@a 
D=A
@p
M=D

// A=contenido de p, pero p tiene la direccion de A
@p
A=M  // A = 16
D=M   // D = contenido de la direccion 16 = 10
@b
M=D  // Guardando en 17 (b) el 10 que esta en D

##Actividad 6
...
## Actividad 7

(start)

//int result = 0;

@result
M=0

/*
int main()
{
  result = sum(3, 4);
  std::cout << "The sum: " << result << std::endl;
}
*/

// Load sum arguments
@3
D=A
@R0
M=D
@4
D=A
@R1
M=D

// Save return address
@returnFromSum
D=A
@R15
M=D

// call sum
@sum
0;JMP

// return after sum
// and store result
(returnFromSum)
@R0
D=M
@result
M=D

@fin
(fin)
0;JMP

/*
int sum(int a, int b)
{
    return a + b;
}
*/

(sum)
@R0
D=M
@R1
D=D+M
@R0
M=D
@R15
A=M
0;JMP

## Actividad 8

```asm
@10
D=A
@a
M=D


@20
D=A
@b
M=D
//Creamos las variables a=10 y b=20 que se asignaran originalmente en R16 y R17 

@a
D=A
@R0
M=D


@b
D=A
@R1
M=D
//Guardamos las variables en los registros R0 (a) y R1 (b)

@return
D=A
@R15
M=D
//Creamos la variable return y le asignamos la posición R15

@swap
0;JMP
//Saltamos a swap 

(return)

@END
(END)
0;JMP
//Fin del programa

(swap)
    @R0
    A=M     
    D=M    
    @TMP
    M=D     


    @R1
    A=M     
    D=M     
    @R0
    A=M     
    M=D    

    @TMP
    D=M  
    @R1
    A=M  
    M=D 

    @R15
    A=M
    0;JMP
    //Saltamos a la pocisión R15 que es return 
    //Creamos función swap, asignando pocisiones temporales
    //El programa intercala el valor de b con el de a en R16 y R17

```

<img width="394" height="193" alt="Captura de pantalla 2026-02-13 142450" src="https://github.com/user-attachments/assets/35688159-e029-41c2-b951-75c0dd67adb0" />

Se muestran los valores de a y b  guardados en R16 y R17 

<img width="859" height="471" alt="image" src="https://github.com/user-attachments/assets/8ae047df-61ee-4375-862f-462656fadb42" />

Se muestran las pocisiones de a y b usadas como puntero para el intercambio 

<img width="824" height="727" alt="Captura de pantalla 2026-02-13 142826" src="https://github.com/user-attachments/assets/16e13cc3-35b1-45a5-896c-eddc057c55f1" />

Valores intercambiados de a y b

```asm
@10
D=A
@arr0
M=D

@15
D=A
@arr1
M=D

@2
D=A
@arr2
M=D

@3
D=A
@arr3
M=D

@50
D=A
@arr4
M=D
//Debemos hacer un arreglo de 5 elementos 
//R0 es la base del arreglo 
//Aquí iniciamos el arreglo, nombramos las variables arr 0-4, y les damos sus valores 

@arr0
D=A
@R0
M=D

@5
D=A
@R1
M=D
//Preparamos la base del arreglo y su longitud, asignando su valor en R0 y R1

@return
D=A
@R15
M=D
@calSum
0;JMP

(return)
@R0
D=M
@sum
M=D
//Creamos funcion return 

@END
(END)
0;JMP




(calSum)
    @SUM
    M=0

    @I
    M=0

(calSum_LOOP)
    @I
    D=M        
    @R1
    D=D-M       
    @calSum_END
    D;JGE       
 //Creamos un ciclo que compara I con R1 (tamaño del arreglo) Si I es mayor, finaliza y salta a la dirección de D

    @R0
    D=M


    @I
    A=M     
    D=D+A        


    @ADDR
    M=D
 //Guardamos el valor en la variable ADDR
    @ADDR
    A=M
    D=M

    @SUM
    M=D+M

    @I
    M=M+1

    @calSum_LOOP
    0;JMP
    
    //Sumamos los arreglos y los guardamos en SUM 

(calSum_END)
    @SUM
    D=M
    @R0
    M=D
    @R15
    A=M
    0;JMP
//Finalizamos el loop
```

<img width="851" height="741" alt="Captura de pantalla 2026-02-13 152416" src="https://github.com/user-attachments/assets/5d4ea655-5e69-40c7-ac00-9313528f872b" />

Guardamos y mostramos en memoria el valor de cada arreglo 

<img width="866" height="861" alt="Captura de pantalla 2026-02-13 163949" src="https://github.com/user-attachments/assets/52e923e6-8893-4564-9ceb-d5478468bb7f" />

De a poco va a sumando, el resultado de la suma por etapas se muestra en R22 
El loop se repite hasta sumar todos los valores de cada arreglo

<img width="857" height="785" alt="Captura de pantalla 2026-02-13 164330" src="https://github.com/user-attachments/assets/fc5d2576-25e1-4a89-a0f8-1b89332843d4" />

El resultado de la suma de los arreglos es 80 y se guarda en R0


## Bitácora de reflexión

## Actividad 9

<img width="1211" height="787" alt="image" src="https://github.com/user-attachments/assets/88975e70-8a6d-4175-90de-01eb51626885" />
Bit map editor design 

```asm
(draw)
	// put bitmap location value in R12
	// put code return address in R13
	@SCREEN
	D=A
	@R12
	AD=D+M
	// row 5
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@30727 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 6
	D=A // D holds previous addr
	@31
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@2033 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	// row 7
	D=A // D holds previous addr
	@31
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@2033 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	// row 8
	D=A // D holds previous addr
	@31
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@2017 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	M=1
	// row 9
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@1985 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@3 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 10
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@1921 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@7 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 11
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@1921 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@15 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 12
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	M=-1
	AD=A+1 // D holds addr
	@15 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 13
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@255 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@12 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 14
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@7743 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@8 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 15
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@12800 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@8 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 16
	D=A // D holds previous addr
	@30
	AD=D+A
	@32767
	A=!A // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@9216 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@24 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 17
	D=A // D holds previous addr
	@30
	AD=D+A
	@16384 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@14336 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@16368 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 18
	D=A // D holds previous addr
	@30
	AD=D+A
	@16384 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1
 AD=A+1 // D holds addr
	@15872 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 19
	D=A // D holds previous addr
	@30
	AD=D+A
	@16384 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@1792 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@15872 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 20
	D=A // D holds previous addr
	@30
	AD=D+A
	@16384 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@1792 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@14400 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 21
	D=A // D holds previous addr
	@30
	AD=D+A
	@24576 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@1792 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@10240 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 22
	D=A // D holds previous addr
	@30
	AD=D+A
	@8192 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@1792 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@14480 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 23
	D=A // D holds previous addr
	@30
	AD=D+A
	@8192 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	M=1
	AD=A+1 // D holds addr
	@6144 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 24
	D=A // D holds previous addr
	@30
	AD=D+A
	@4096 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@3 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@3072 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 25
	D=A // D holds previous addr
	@30
	AD=D+A
	@4096 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@7 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	@1536 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 26
	D=A // D holds previous addr
	@30
	AD=D+A
	@2048 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@8065 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@1023 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 27
	D=A // D holds previous addr
	@30
	AD=D+A
	@2048 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	M=-1
	AD=A+1 // D holds addr
	@3 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	// row 28
	D=A // D holds previous addr
	@30
	AD=D+A
	@4608 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@2047 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	M=1
	// row 29
	D=A // D holds previous addr
	@30
	AD=D+A
	@30721 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	@2047 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	M=1
	// row 30
	D=A // D holds previous addr
	@31
	AD=D+A
	@2047 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	M=1
	// row 31
	D=A // D holds previous addr
	@31
	AD=D+A
	@2044 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=D-A // RAM[addr] = val
	AD=A+1 // D holds addr
	M=1
	// row 32
	D=A // D holds previous addr
	@31
	AD=D+A
	@8 // A holds val
	D=D+A // D = addr + val
	A=D-A // A=addr + val - val = addr
	M=A-D // RAM[addr]=-val
	AD=A+1 // D holds addr
	M=1
	// return
	@R13
	A=M
	D;JMP

//Esta wea esta muy largaaaaa
```












