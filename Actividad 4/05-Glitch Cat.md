## Reto
Glitch Cat

## Descripcion
Our flag printing service has started glitching!

## Solucion
- Al empezar el desafio nos dan el siguiente comando `$ nc saturn.picoctf.net 53129` 
- Al ponerlo en el webshell nos dio lo siguiente: `'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'`
- Se puede ver que esta es la bandera pero parte de ella esta puesta como chr de ASCII
- Usando cyberchef transforme cada caracter a lo siguiente:
					0x62 - b
					0x64 - d
					0x61 - a
					0x36 - 6
					0x38 - 8
					0x66 - f
					0x37  - 7
					0x35 - 5

- Cambie los carecteres y me quedue con la bandera correcta: **picoCTF{gl17ch_m3_n07_bda68f75}**

## Notas
- El ejercicio 01 ayuda a la solucion de este al saber como convertir hezadecimal a ASCII


## Referencias
[CyberChef](https://gchq.github.io/CyberChef/)

