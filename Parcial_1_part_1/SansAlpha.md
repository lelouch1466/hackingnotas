
## Reto
SansAlpha
## Descripcion
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.

## Solucion
- cuando entramos al sistema estamos en una terminal que solo acepta simbolos y numeros, nada de letras
- empezamos por inspeccionar el directorio actual con `./*` para que aparescan todos los archivos
- nos damos cuenta de que la terminal solo imprime 1 cosa por comando y que hay una carpeta llamada *blargh*
- como no podemos usar comandos de forma normal, usaremos **wildcards** que son basicamente los mismos que usamos en regex.
- como sabemos que blargh es un directorio intentaremos ver que hay adentro con:
```
./*/*
```
- lo que encontramos es que ahi esta la bandera pero tenemos 2 problemas
	1. tenemos el acceso denegado a esta
	2. no tenemos comandos para abrila con wildcards
- para enfrentar estos 2 problemas usaremos los wildcards para hacer nuestros propios comandos
- sin acceso directo a un archivo lo que se puede hacer es cifrarlo a base64, imprimirlo y luego lo desciframos usando otro programa
- para cifrar algo a base64 se usa el comando `base64` que esta en la carpeta `/bin/base64` para asignar esto a un comando hacemos:
```
_1=(/???/????64)
```
- ? = 1 cararter el que sea
- con los signos de interrogacion el sistema buscara algo de 3 caracteres en raiz y que adentro tenga algo de 4 caracteres que le siga de "64" y el unico que encuentra es /bin/base64, y a esta carpeta se le asigna `_1`
- ahora podemos usar los comandos dentro de base64 usando `_1` pero como hay mas de 1 comando tenemos que especificar cual de esta forma:
```
"${_1[0]}" ./??????/????.???
```
- con esto es lo mismo que decirle
```
base64 ./blargh/flag.txt
```
- nos devuelve un cifrado en base64:
```
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV82NDBiNmFkZH0=
```
- al ponerlo en cybershef obtenemos la bandera: **picoCTF{7h15_mu171v3r53_15_m4dn355_640b6add}**
## Notas

## Referencias
[PicoCTF 2024 SansAlpha Challenge solve | by Virtu4l | Medium](https://medium.com/@0xVirtu4l/picoctf-2024-sansalpha-challenge-solve-c754ee1deba4)