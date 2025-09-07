## Reto
blame game
## Descripcion
Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/156/challenge.zip)

## Solucion
- Despues de descargar y descomprimir el archivo me da un directorio
- Dentro del directorio solo se puede ver un .py pero si pongo cd[tab] me da el directorio de git
- Dentro de la carpeta de git exploro usando `ls` para encontrar algo que me sirva o me paresca relevante
- Encuentro la carpeta de logs que puede tener infomacion util del historial del git
- Dentro encuentro un archivo HEAD, le doy un `cat HEAD`, me salen muchas lineas con "picoCTF <ops@picoctf.com> 1710202021 +0000    commit: important business work" y entre todas ellas es facil ver que esta la bandera ahi:
  **picoCTF{@sk_th3_1nt3rn_d2d29f22}**

## Notas
- no siento que esta fuera la forma de encontrar la bandera
- Despues de jugar un poco recorde grep y asi es mas facil encontrarla una vez dentro de la carpeta git

## Referencias
