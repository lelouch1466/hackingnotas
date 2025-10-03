
## Reto
SQLiLite

## Descripcion
Can you login to this website?

Additional details will be available after launching your challenge instance.

## Solucion
- al entrar a la pagina aperece un formulario de loggeo
- al poner cualquier cosa me sale si entre o no pero tambien la sentencia sql que se hizo
- hago una inyeccion en sql poniendo `' or 1=1;` en contraseña y me deja entrar
- ahora me dice si puedo ver la bandera, inspecciono los elementos y esta en una parrafo con hidden para que no se vea: `< p  hidden="">Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_ec8a64c7}</p>`

## Notas

## Referencias
