
## Reto
Operation Oni
## Descripcion
Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

Additional details will be available after launching your challenge instance.
## Solucion
- nos dicen que nos conectemos a un sistema pero no tenemos la llave privada
- pero nos dieron una imagen del disco del sistema que corre el ssh
- entonces le hacemos el `gunzip` y buscamos las particiones con `fls`
- vemos que en una particion al buscar el root encontramos el .ssh
- cuando abrimos esa carpeta encontramos 2 id, al abrirlas con `icat` vemos que 1 tiene la llave privada
- la guardamos en nuestro sistema local con
```
icat -o 206848 disk.img 2345 > file
```
- ya tenemos la llave pero si tratamos de conectarnos con ssh al sistema, este no lo acepta porque file (donde guardamos la llave) es muy abierto
- tenemos que restringirlo para solo el super usuario con
```
chmod 600 file
```
- y ahora si intentamos conectarnos logramos entrar
- ya dentro del sitema solo hacemos ls y un cat para encontrar y abrir la bandera:**picoCTF{k3y_5l3u7h_af277f77}**
## Notas
- en clase no entendi mucho que estabamos haciendo pero con la guia si medio entendi porque se hacian las cosas
## Referencias
[PICOCTF Challenge Writeup (Operation Oni) | by Umer Waqar | Medium](https://medium.com/@brownguy231256/picoctf-challenge-writeup-operation-oni-41fded2b3ba9)