
## Reto
### Picker I
## Descripcion
This service can provide you with a random number, but can it do anything else?Connect to the program with netcat:`$ nc saturn.picoctf.net 54019`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/514/picker-I.py).
## Solucion
- al entrar al netcat me dice esto
```
Try entering "getRandomNumber" without the double quotes...
```
- tal parece ser el nombre de una funcion, y si esa funcion esta en el progama se va a ejecutar
- al revisar el codigo fuente a pesar de que tiene muchas cosas raras veo la funcion `win()`
- me vuelvo a conectar al netcat y le digo que corra win, lo que me devuelve un cifrado en hexa, que cuando lo pongo en cybershef me da la bandera: **picoCTF{4_d14m0nd_1n_7h3_r0ugh_6e04440d}**
```
Try entering "getRandomNumber" without the double quotes...
==> win 
0x70 0x69 0x63 0x6f 0x43 0x54 0x46 0x7b 0x34 0x5f 0x64 0x31 0x34 0x6d 0x30 0x6e 0x64 0x5f 0x31 0x6e 0x5f 0x37 0x68 0x33 0x5f 0x72 0x30 0x75 0x67 0x68 0x5f 0x36 0x65 0x30 0x34 0x34 0x34 0x30 0x64 0x7d 
```
## Notas

## Referencias
