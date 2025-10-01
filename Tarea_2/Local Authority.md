
## Reto
Local Authority

## Descripcion
Can you get the flag?

Additional details will be available after launching your challenge instance.

## Solucion
- al entrar a la pagina hay 2 cuadros de texto que preguntan por usuario y contaseña
- al inspeccionar los elemntos no se ve ni siquiera un script
- pongo valores cualquiera y me manda a una pagina con "loggin failed"
- checo los elemntos en esta pagina y veo que ahora hay un script
- aunque esta la logica para el filtro, la funcion que checa la contraseña "checkpassword" no la encuentro aqui
- me voy a la pestaña de network y al recargar la pagina encuentro secure.js y al abrirlo en preview encuentro la funcion checkpassword y veo que checa por admin con contraseña strongPassword098765
- los pongo en la pagina y me da la bandera **picoCTF{j5_15_7r4n5p4r3n7_b0c2c9cb}**

## Notas
- tuve que ver una solucin para ver donde se encontraba el .js que buscaba
## Referencias
[Local Authority PicoCTF 2022. In this Easy Web Exploitation CTF tests… | by Zarar Ahmed | Medium](https://zarrarkolachi.medium.com/local-authority-picoctf-2022-bcce6f1b142f)