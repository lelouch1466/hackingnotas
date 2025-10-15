
## Reto
### tunn3l v1s10n
## Descripcion
We found this [file](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n). Recover the flag.
## Solucion
- si al descargar el archivo le hacemos exiftool vemos que es un .bmp
- pero no nos deja abrirlo incluso si cambiamos su extencion
- tenemos que abrir el hexedito y cambiarle unos cuantos bits
- despues de seguir la guia y no tener ni idea de que estoy haciendo, cambie los bits necesarios y ya se abrio la imagen con la bandera : **picoCTF{qu1t3_a_v13w_2020}**



## Notas
- Oficialmente cualquier reto que tenga que ver con bits y hexeditor lo odio 
- con la guia al menos ahora entendi donde estan los offset, pero no entiendo porque van de 10 en 10

## Referencias
[tunn3l_v1s10n — PicoCTF 2021. This challenge didn’t bore me and… | by Ganesh Datta | Medium](https://gddaredevil.medium.com/tunn3l-v1s10n-picoctf-2021-22af85aab8dc)