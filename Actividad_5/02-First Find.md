## Reto
First Find
## Descripcion
Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/500/files.zip)

## Solucion
- Primero descargo el archivo y lo descomprimo
- Hago este comando `grep -r 'uber' files` para tratar de encontrar el archivo pero me salen muchas coincidencias
- Hago un --help para ver si puedo filtrar por nombre de archivo y encuentro que -l lo hace
- Ahora corro `grep -rl 'uber' files` pero no me aparece el archivo que busco
- Pense que tal vez se deba a que el archivo esta oculto y grep no busca los archivos ocultos, busco en --help para ver si hay una opccion para buscar en ocultos pero no la encuentro.
- Sin saber que hacer pongo `grep -rL 'uber' files` y  de alguna forma si me aparece la direccion del archivo¯\ _ (ツ) _ /¯
- Ya solo lo abro con `less ~/files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt` y obtengo la bandera **picoCTF{f1nd_15_f457_ab443fd1}**

## Notas
- Sigo sin entender como es que sirvio -L para encontrar el archivo pero -l no sirvio
- Busque tutoriales despues de resolver el desafio y tal parece que tenia que usar find

## Referencias
[First Find |PicoCTF challenge |walkthrough](https://www.youtube.com/watch?v=eDpyR-CjXak)