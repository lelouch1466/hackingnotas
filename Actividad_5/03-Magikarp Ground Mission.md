## Reto
Magikarp Ground Mission

## Descripcion
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `b60940ca`

## Solucion
- Al principio me dan el comando: ` ssh ctf-player@venus.picoctf.net -p 55175` para conectarme con ssh a ubuntu
- Una vez dentro utilizo ls y cat para abrir los .txt y encontrar partes de la contraseña
- Primero abro la primera parte de la bandera, y despues uso cd / para ir a donde esta la siguiente parte
- Despues encuentro la segunda parte de la bandera con ls y la abro con cat, y uso cd ~ para ir a donde esta la ultima parte
- Finalmente uso ls y cat para abrir la ultima parte de la bandera y me queda: **picoCTF{xxsh_0ut_0f_\/\/4t3r_c1754242}**

## Notas
- Al principio no entendia como entrar a ubuntu con ssh hasta que vi que me daban el comando desde un principio
- Es el primer desafio donde uso cat para abrir .txt, ya que lo vi soluciones de desafios anteriores
- Ya sabia usar ls y cd

## Referencias



