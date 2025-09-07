## Reto

## Descripcion
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/19/challenge.zip)

`ssh -p 50399 ctf-player@atlas.picoctf.net`Using the password `1db87a14`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!

## Solucion
- Una vez que nos conectamos al servidor se corre el programa del desafio que nos dice que encontremos un numero entre 1 y 1000
- Cada vez que nos conectamos el numero es diferente y las pistas que nos dan es que una vez adivinemos un numero nos dira si es mas grande o mas chico el numero correcto
- Con este conocimiento partiremos en mitades, primero adivinaremos 500, si nos dice mas bajo el siguiente sera 250, si dice mas alto 750.
- Despues seguiremos adivinando de mitad en mitad, en mi caso los numero introduje fueron: 500->250->125->62->31(mas alto, entre 62 y 31)->46->38->34
- Cuando puse 34 ese era el numero y me dio la bandera: **picoCTF{g00d_gu355_1597707f}**

## Notas
- Usando este metodo y por el numero de intentos que te dan, no importa cual sea el numero, esta garantizado que para el 10mo intento lo hayas encontrado
- Este metodo me recuerda a los alogaritmos de ordenamiento en programacion, mas especificamente a merge y quick sort.
## Referencias
