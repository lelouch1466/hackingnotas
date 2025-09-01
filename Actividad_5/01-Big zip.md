## Reto
Big zip

## Descripcion
Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/505/big-zip-files.zip)

## Solucion
- Trate de usar grep en el zip descargado para encontrar 'pico' pero no me dio ningun resultado
- Use `grep --help` para ver si se podia usar grep sobre archivos lo que me dio -r que hace grep recursivamente sobre todos los directorios que encontre dentro de 1 carpeta
- Al tratar de usar grep -r sobre  el zip este no sirve y porque tengo que descomprimirlo primero
- despues de descomprimir el zip uso `grep -r 'pico' big-zip-files` y me regresa la bandera **picoCTF{gr3p_15_m4g1c_ef8790dc}**

## Notas
- Antes de descomprimir el zip no sabia que debia deescomprimirlo primero y me quede trabado hasta que vi un tutorial
- Aprendi a como descomprimir un zip

## Referencias
[First Find & Big Zip <grep> - HackMD](https://hackmd.io/@nataliepjlin/SknjWeri3)