
## Reto
### byp4ss3d
## Descripcion
A university's online registration portal asks students to upload their ID cards for verification. The developer put some filters in place to ensure only image files are uploaded but are they enough? Take a look at how the upload is implemented. Maybe there's a way to slip past the checks and interact with the server in ways you shouldn't.

Additional details will be available after launching your challenge instance.
## Solucion
- la pagina nos deja subir archivos de imagen como .png o .jpg
- si intentamos alguna otra forma de archivo no dice "Not allowed!"
- Pero no se fija si en realidad es .png, solo se fija en la extencion .png
- la pista que nos dan dice que podemos engañar a apache para que lea un archivo como si fuera php con el .htaccess
- primero creo un archivo que le llamo `.htaccess` y dentro de esto le pongo lo siguiente:
```
AddType application/x-httpd-php .png
```
- esto le dice que interprete .png como un php
- cuando intento subirlo no lo veo, doy click derecho y le pongo `show hidden files` para que aparesca mi .htaccess
- ahora trato de subirlo y o sorpresa si sirvio


-imagen aqui

- ahora puedo ir a [http://amiable-citadel.picoctf.net:49481/images/.htaccess] , aqui estoy tratando de abrir mi archivo que esta subido, pero en realidad lo que hice fue inyectar la pagina .htaccess y por eso cuando lo abro no me dice hay un error con la imagen(ver **sidenote**), si no que tengo el acceso restringido
-imagen aqui

- Ahora con el .htaccess que le dice a apache interpretar .png como php puedo aprovecharme de esto
- creo un archivo de texto y adentro pongo php para un webshell(codigo en referencias) y lo llamo "simple.png"
- regreso a la pagina para subir archivos, trato de subirlo y me deja porque piensa que es un png
- ahora si voy a la pagina que lo contiene para verlo(http://amiable-citadel.picoctf.net:62538/images/simple3.png) me abre un webshell
-imagen aqui

- igual que en el desafio de **Trickster**, no puedo aplicar cd, pero puedo encontrar cosas con `find` entonces aplico este comando:
```
find / -name *.txt
```
- con esto busco desde root cualquier .txt para ver como se llama y donde esta y obtengo esto:

-imagen aqui

- a muchos tengo permiso denegado, pero vero uno `/var/www/flag.txt` al que puedo acceder y es mi bandera
- para verla solo pongo en el webshell
```
cat /var/www/flag.txt
```
- y obtengo mi bandera: **picoCTF{s3rv3r_byp4ss_20193d1e}**

#### sidenote
- si intentaba abrir mi simple.png me salia este error:
-imagen aqui

## Notas

## Referencias
[easy-simple-php-webshell.php](https://gist.github.com/joswr1ght/22f40787de19d80d110b37fb79ac3985)
