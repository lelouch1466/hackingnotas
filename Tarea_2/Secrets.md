
## Reto
Secrets

## Descripcion
We have several pages hidden. Can you find the one with the flag?

Additional details will be available after launching your challenge instance.

## Solucion
- al entrar a la pagina no se ve nada interesante ni en los elementos ni en las otras paginas
- en la pagina de about veo que tiene una imagen e inspecciono los elemntos ahi pero no se me nada
- busco en sources y veo que la imagen viene de secret/assets
- en web puedo interpretar la carpeta como un directorio entonces pongo [link]/secret/
- me envia a una pagina que dice que casi encuentro la bandera al ver sources de nuevo ahora aparece hidden y voy a [link]/secret/hidden/
- aparece una pagina como para loggearse a algo y en sources ahora esta superhidden entonces ahora voy a [link]/secret/hidden/superhidden/
- aparece una pagina donde dice que la encontre pero no se ve nada, puedo seleccionar toda la pagina para que aparesca texto del mismo color que el fondo o revisando los elementos de la pagina aparece la bandera: **picoCTF{succ3ss_@h3n1c@10n_51b260fe}**

## Notas
- la pagina de hidden si me saco de onda porque pensaba que me fui a otra pagina que me estaba poniendo virus xD

## Referencias
[picoCTF — Secrets (Web Exploitation) Challenge Explained | by MoRoMeR | Medium](https://medium.com/@moromerx/picoctf-secrets-web-exploitation-explained-3e8d41b40a2a)