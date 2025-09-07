
## Reto
PW crack 3
## Descripcion
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/16/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/16/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/16/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

## Solucion
- igual que en los otros 2 pw crack, despues de descargar el archivo le aplico un `nano level3.py`, y se ve que hay 7 posibles contraseñas
- Copie las posibles contraseñas en un block de notas (6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e) y corri el programa poniendo cada contraseña hasta que atinarle a la buena y me dio la bandera **picoCTF{m45h_fl1ng1ng_2b072a90}**


## Notas
- Las pistas referian a usar `bvi` para leer el binario del hash, pero trate de usar cybershef y no me salia nada
- Despues de resolverslo busque soluciones para ver si usaban bvi, pero ninguna lo usaba, en vez de eso modificaban el codigo del archivo con un ciclo para no tener que poner las contraseñas una por una.
- Aun no entiendo para que era la pista de biv

## Referencias
