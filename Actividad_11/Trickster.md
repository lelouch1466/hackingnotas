
## Reto
Trickster

## Descripcion

## Solucion
- Al abrir la pagina solo es una pagina para subir png
- Si vamos al robots.txt vemos que hay ptra pagina de 'instructions.txt'
- Si la abrimos vemos que son las instrucciones de que hace la pagina y como lo hace y nos dice 2 cosas importantes:
	1. checa que tenga '.png' en la extencion
	2. checa que los bits magicos (los que identifican el archivo) empieze con PNG

- sabiendo esto podemos subir un archivo disfrazandolo como png
- Creo un archivo php usando `nano simple.php` y dentro copio un webshell(link en referencias)
- Dentro del archivo pongo en la primera linea 'PNG' y me queda algo asi:
<img width="436" height="204" alt="image" src="https://github.com/user-attachments/assets/d071fa91-612d-4cf4-8100-f11b6b86bbef" />

- Tambien cambio el nombre del archivo para que contenga la extencion .png pero siga siendo .php usando `mv simple.php simple.png.php`
- Ahora trato de subirlo a la pagina y me sale que fue exitoso
- ahora para abrirlo desde la web se guarda en `[link_de_pagina]/uploads/[nombre_archivo]` 
- una vez que abro la pagina me sale esto:
<img width="862" height="130" alt="image" src="https://github.com/user-attachments/assets/2f2e8b9a-b14a-40df-8c30-b66605fef198" />

- esto funciona como un webshell y puedo poner comandos
- si uso ls solo me sale el archivo que subi
- uso `find -name *.txt` para encontrar los txt que haya en la pagina y encuentro uno raro con puras letras mayusculas
- copio su directorio y lo abro con cat y obtengo la bandera: **picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_d3ac625b}**

## Notas
- me perdi al tratar de seguir la soluncion en clase porque no entendi donde se guardaba lo subido
- 

## Referencias
[picoCTF 2024: Trickster. Tags: Web Exploration… | by Altair | Medium](https://medium.com/@niceselol/picoctf-2024-trickster-af90f7476e18)
[easy-simple-php-webshell.php](https://gist.github.com/joswr1ght/22f40787de19d80d110b37fb79ac3985)
