
## Reto
### findme
## Descripcion
Help us test the form by submiting the username as `test` and password as `test!`The website running [here](http://saturn.picoctf.net:63430/).

## Solucion
- al entrar a la pagina hay un formulario de usuario y contraseña
- si ponemos datos dummys nos aparece que usemos `user:test password:test!`
- cuando lo ponemos y damos enter nos dirije a una pagina que dice fue reedirigido aqui para encontrar la bandera, hay un bloque de tecto pero no nos da nada
- usando foxyproxy y burp usando intercept al entrar a la pagina encuentro que al hacer foward no llego a la pagina de antes
- si doy foward de nuevo sigo sin llegar a la pagina
- me doy cuenta que al dar enter me redirije a un link que me redirije a otro link
- examino los links que me rediren:
```
http://saturn.picoctf.net:63430/next-page/id=cGljb0NURntwcm94aWVzX2Fs
http://saturn.picoctf.net:63430/next-page/id=bF90aGVfd2F5X2RmNDRjOTRjfQ==
```
- veo que si junto los id se forma un cifrado en base64
- al ppnerlo en cybershef obtengo la bandera: **picoCTF{proxies_all_the_way_df44c94c}**

## ALT 
- en vez de usar burp, solo abri la pagina y entre con el user y password que me dan
- despues reviso mi historial y copio los ultimos 2 links que tengo

## Notas

## Referencias
[picoCTF Web Exploitation: findme. Ready to explore another picoCTF… | by Kamal S | Medium](https://medium.com/@Kamal_S/picoctf-web-exploitation-findme-a471621624b3)
