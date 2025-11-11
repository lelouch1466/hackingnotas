
## Reto
### Picker IV
## Descripcion
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 58618`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/527/picker-IV.c). The binary can be downloaded [here](https://artifacts.picoctf.net/c/527/picker-IV).
## Solucion
- desde un principio, que me dieran el binario del programa ya me hacia sospechar de algo
![](../Imagenes/Pasted%20image%2020251111050034.png)
- al conectarme al netcat me sale lo siguiente:
```
Enter the address in hex to jump to, excluding '0x':
```
- eso junto con el echo del binario ya me dijo que es exactamente que debia hacer
- igual que en los desafios de [PIE TIME](../Desafios_extra/PIE%20TIME.md), debo encontrar la direccion de la funcion win
- sobre el binario aplico este comando que es el mismo que aplico en los retos de PIE
```
readelf -s picker-IV | egrep '\b(main|win)\b'  
```
- me da la direccion de donde esta win
- ahora solo me conecto al netcat y pongo la direccion que encontre para que me den la bandera:**picoCTF{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_01672a61}**
![](../Imagenes/Pasted%20image%2020251111050453.png)
## Notas
- el echo de que los desafio se pie time me hayan servido para este me alegro porque los de pie time son de mis favoritos que eh echo :)

## Referencias
