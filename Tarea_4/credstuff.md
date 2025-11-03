
## Reto
### credstuff
## Descripcion
We found a leak of a blackmarket website's login credentials. Can you find the password of the user `cultiris` and successfully decrypt it?Download the leak [here](https://artifacts.picoctf.net/c/151/leak.tar).The first user in `usernames.txt` corresponds to the first password in `passwords.txt`. The second user corresponds to the second password, and so on.
## Solucion
- primero al descargar el archivo es un .tar y para descomprimirlo uso `tar -xf`
- nos dicen que el usuario 1 corresponde a la contraseña 1 y asi sucesivamente
- debemos encontar el numero de linea donde esta el usuario `cultiris` y lo hago usando este grep
```
lelouch1466-picoctf@webshell:~/leak$ grep -n 'cultiris' usernames.txt 
378:cultiris
```
- veo que esta en la linea 378, entonces imprimo la linea 378 de passwords.txt asi:
```
lelouch1466-picoctf@webshell:~/leak$ sed -n '378p' passwords.txt 
cvpbPGS{P7e1S_54I35_71Z3}
```
- veo que tiene las llaves de la bandera y facilmente veo que esta en algun ROT, lo pongo en cybershef y me regresa la bandera: **picoCTF{C7r1F_54V35_71M3}**
## Notas
- tambien pude haber echo un `grep '{' passwords.txt` para encontrar la bandera

## Referencias
