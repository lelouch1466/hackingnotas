
## Reto
 Scavenger Hunt
## Descripcion
There is some interesting information hidden around this site [http://mercury.picoctf.net:39698/](http://mercury.picoctf.net:39698/). Can you find it?
## Solucion
- Al entrar a la pagina no se ve nada interesante, al inspeccionar los elementos vemos que en un comentario esta la primera parte:
~~~
/ <!-- Here's the first part of the flag: picoCTF{t -->

~~~
- A continuacion entro al CSS y encuentro la segunda parte:
~~~
/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */
~~~
- Ahora entro al script pero no encuentro la bandera si no una pista:   
/ How can I keep Google from indexing my website? /
con esto busco en el robots porque es ahi donde google no idexa la pagina, asi que voy a [mercury.picoctf.net:39698/robots.txt](http://mercury.picoctf.net:39698/robots.txt) y encuentro la tercera parte y la siguiente pista:
~~~
# Part 3: t_0f_pl4c
# I think this is an apache server... can you Access the next flag?
~~~

- Como me dice que es un servidor de apache uso .htaccess para ver los directorios y subdirectorios desde el mismo directorio, asi que pongo [mercury.picoctf.net:39698/.htaccess](http://mercury.picoctf.net:39698/.htaccess) y encuentro la cuarta parte y la siguiente pista:
~~~
# Part 4: 3s_2_lO0k
# I love making websites on my Mac, I can Store a lot of information there.
~~~
- Como dice que lo hizo desde una Mac, si lo subio sin modificar archivos tal vez tambien subio el .DS_Store que es donde macOS guarda bastantes cosas importantes, voy a [mercury.picoctf.net:39698/.DS_Store](http://mercury.picoctf.net:39698/.DS_Store) y encuentro la ultima parte:
~~~
Congrats! You completed the scavenger hunt. Part 5: _fa04427c}
~~~
- Al juntar todo tengo la bandera: **picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_fa04427c}**
## Notas
- Aun no entiendo muy bien el .htaccess y el .DS_Store
## Referencias
[Apache HTTP Server Tutorial: .htaccess files - Apache HTTP Server Version 2.4](https://httpd.apache.org/docs/2.4/en/howto/htaccess.html)
[.DS_Store - Wikipedia](https://en.wikipedia.org/wiki/.DS_Store)