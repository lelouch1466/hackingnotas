## Reto
First Grep

## Descripcion
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/495d43ee4a2b9f345a4307d053b4d88d/file)? This would be really tedious to look through manually, something tells me there is a better way.

## Solucion
Primero intente usar regex para encontar un patron igual a la primera linea del archivo *yQE:Z:y?9U@Z*  usando este regex: `...:.:......`
y si me dio 1 coincidencia SYb:5:[`$^&l
pero no era la respuesta.

Despues busque tutoriales y vi que las opciones mas comunes para buscar en este problema son root,pass o pico.
Al buscar con pico encontre la bandera que es **picoCTF{grep_is_good_to_find_things_dba08a45}**

## Notas
- Se aprendio un poco de como funciona regex
- Se aprendio que es lo que se debe estar buscando en estos desafios

## Referencias
[Learn Grep and Regular Expressions with examples - Linux Tutorial](https://ryanstutorials.net/linuxtutorial/grep.php)
[regex101: build, test, and debug regex](https://regex101.com/)
[RegExr: Learn, Build, & Test RegEx](https://regexr.com/)
[picoCTF 2019 — First Grep. Hello People … 👋 | by Waltech Academy | Medium](https://medium.com/@walterchristian28/picoctf-2019-first-grep-601cced5392a)
