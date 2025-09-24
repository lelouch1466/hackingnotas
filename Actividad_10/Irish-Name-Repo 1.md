
## Reto
Irish-Name-Repo 1

## Descripcion
There is a website running at `https://jupiter.challenges.picoctf.org/problem/39720/` ([link](https://jupiter.challenges.picoctf.org/problem/39720/)) or http://jupiter.challenges.picoctf.org:39720. Do you think you can log us in? Try to see if you can login!

## Solucion
- inspecciono los elementos de la pagina para analizar los formularios del loggin
- veo que hay un cuarto input oculto, le cambio el tipo de 'hidden' a 'form' y ahora al tratar de entrar me da la sentencia SQL que se envia.
- Viendo la sentencia veo que puedo hacer una inyeccion SQL entonces ahora en username pongo: ' *admin'; 1=1;*  ' lo que cambia la sentencia a esto:
~~~
  SELECT * FROM users WHERE name='admin' or 1=1;' AND password='admin'
  ~~~
- con esto "AND password" lo ignora, me deja entrar y me da la bandera **picoCTF{s0m3_SQL_c218b685}**
## Notas

## Referencias
[SQL Injection](https://www.w3schools.com/sql/sql_injection.asp)
