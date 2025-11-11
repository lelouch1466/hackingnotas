
## Reto
### Picker III
## Descripcion
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 58308`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/525/picker-III.py).
## Solucion
- al conectarme al programa tal parece que no hay nada
- si pongo algo me dice que intente "help"
- cuando lo pongo me sale que puedo poner un numero para realizar opciones: 
```
* Enter 'quit' to quit the program.
* Enter 'help' for this text.
* Enter 'reset' to reset the table.
* Enter '1' to execute the first function in the table.
* Enter '2' to execute the second function in the table.
* Enter '3' to execute the third function in the table.
* Enter '4' to execute the fourth function in the table.

Here's the current table:
  
1: print_table
2: read_variable
3: write_variable
4: getRandomNumber
```
- revisando el codigo fuente puedo ver que existe la funcion win() que tiene la bandera
- viendo la pista me doy cuenta que lo que debo hacer es que alguna de las opciones que me den, en vez de apuntar a su funcion, reenvien a la funcion win()
- para esto uso su funcion write_variable
- write_variable se supone solo escribe una variable y le pone un numero, pero tambien reescribe variables por otro variable
- podemos hacer que cuando nos preguntre por el nombre de una variable le demos el nombre de una funcion que se corra en el menu y reescribirla para que ahora hago lo mismo que win()
![](../Imagenes/Pasted%20image%2020251111055302.png)
```
Here's the current table:
  
1: print_table
2: read_variable
3: write_variable
4: getRandomNumber
==> 3
Please enter variable name to write: read_variable
Please enter new value of variable: win
==> 2
0x70 0x69 0x63 0x6f 0x43 0x54 0x46...
```
- asi en mi caso le dije que read_variable sea igual a win, lo que hizo que ahora que corra read_variable me de un codigo en hex
- al ponerlo en cybershef me dio la bandera: **picoCTF{7h15_15_wh47_w3_g37_w17h_u53r5_1n_ch4rg3_a186f9ac}**

## Notas
- en verdad no entiendo muy bien la logica de este desafio, y lo que escribi fue mi interpretacion de que es lo que paso
## Referencias

[Picker-I, II, III: Walkthrough. Currently, I am doing the past PicoCTF… | by Sunya | Medium](https://medium.com/@sunya22839/picker-i-ii-iii-c77180480482)