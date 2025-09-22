
## Reto
GET aHEAD

## Descripcion
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:28916/](http://mercury.picoctf.net:28916/)

## Solucion
- Al entrar a la pagina solo hay 2 botonesque cambian el color de la pantalla
- al inspeccionar los elementos no se ve nada muy interesante
- vemos que hay 2 formularios con GET y POST
- usando `curl -X GET http://mercury.picoctf.net:28916/` simulamos presionar el boton rojo en consola
- Viendo los tipos de request intentamos simular un request con HEAD
- usando el comando `curl -I http://mercury.picoctf.net:28916/` para simular el HEAD me regresa la bandera: **picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}
**

### ALT
- usando foxyproxy y burp suite puse un proxy y lo intercepte con burpsuite, despues modifique el formulario para que sea HEAD y al enviarlo me regreso la bandera

## Notas
- estuve usando la consola desde kali en mi VM

## Referencias
[HTTP request methods - HTTP | MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Methods)
