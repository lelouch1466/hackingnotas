## Reto
plumbing

## Descripcion
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 14291`.
## Solucion
- Al tratar de conectarse al host que nos da se corre un programa que sobrecarga la terminal con mensajes que no son la bandera.
- Para combatir esto debemos de hacer una tuberia con los comandos para que el primer comando corra fuera de la terminal y el resultado final se mande al segundo comando.
- Use el comando `nc jupiter.challenges.picoctf.org 14291 | grep 'pico'` de esta forma el resultado que me da el primer comando se le aplica un regex buscando la palabra 'pico' y como resultado obtuve la bandera: **picoCTF{digital_plumb3r_ea8bfec7}**
## Notas
- necesite de haber entendido como funcionan los retos 04 y 09 para poder realizar este desafio
- De igual forma supe que el regex que tenia que buscar era 'pico' por el reto 04

## Referencias
[All about pipes, by The Linux Information Project (LINFO)](https://www.linfo.org/pipes.html)