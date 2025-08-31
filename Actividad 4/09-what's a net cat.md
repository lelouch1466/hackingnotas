## Reto
what's a net cat?

## Descripcion
Using netcat (nc) is going to be pretty important. Can you connect to `jupiter.challenges.picoctf.org` at port `64287` to get

## Solucion
- Trate de leer el tutorial dado de como usar net cat pero no lo entendi muy bien y trate de usar este comando: `nc -s jupiter.challenges.picoctf.org 64287` que no funciono
- Busque un tutorial del problema y resulta que estaba casi bien, solo tenia que quitar -s para realizar el comando: `nc jupiter.challenges.picoctf.org 64287` lo cual me dio como resultado la bandera: **You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_284be8f7}**

## Notas
- Aun no tengo muy claro como usar bien las opciones de nc, solo tengo entendido que primero va el nombre del host y despues el puerto
- Se hizo primero este desafio antes de 06-Nice netcat
## Referencias
[nc(1): arbitrary TCP/UDP connections/listens - Linux man page](https://linux.die.net/man/1/nc)
[picoCTF — what’s a net cat. what’s a net cat is a pycoGym challenge… | by USKI | Medium](https://0uski.medium.com/picoctf-whats-a-net-cat-71a7ae4ff4c0)