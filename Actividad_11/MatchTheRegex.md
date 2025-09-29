
## Reto
MatchTheRegex

## Descripcion
How about trying to match a regular expression

Additional details will be available after launching your challenge instance.

## Solucion
- al abrir la pagina nos sale un cuadro que nos dice introducir un input valido
- Al inspeccionar los elementos de la pagina vemos que la parte del script dejaron el regex necesario en un comentario: *^p.....F!?*
	- "^p" -> que empiece con 'p'
	- "....." -> 5 caracteres(1 punto = 1 caracter) los que sean
	- "F!?" -> F mayuscula que puede ir seguida o no de !
- sabiendo esto pongo en el cuadro "pasdfgF" y ya me sale la bandera: **picoCTF{succ3ssfully_matchtheregex_2375af79}**

## Notas
- ya sabia un poco de regex para entender los puntos y ?, pero no sabia ! y resulta que no era nada, pero use una pagina para ver que era

## Referencias
[regex101: build, test, and debug regex](https://regex101.com/)