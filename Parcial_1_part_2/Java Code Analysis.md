
## Reto
### Java Code Analysis!?!

## Descripcion
BookShelf Pico, my premium online book-reading service.I believe that my website is super secure. I challenge you to prove me wrong by reading the 'Flag' book!
## Solucion
- al empezar el desafio nos dan una pagina a la que podemos acceder usando "user" como usurio y contraseña pero tambien nos dan todo el codigo fuente de la pagina
- vemos que hay un libro "flag" pero cuando vamos a esa pagina nos sale que esta bloqueada y solo admin puede verlo
- reviso las cookies pero no tengo nada guardado para la pagina
- si voy a los elementos de la pagina y voy a `Application` puedo que que hay una parte de `Storage`
- ![[Pasted image 20251008124535.png]]
- cuando doy click en este me aparece *Local Storage* y doy click en ahi para que me aparesca los tokens de autenticidad
- veo que es lo mismo que en el reto **JaWT Scratchpad** entonces primero copio el JWT y voy a la pagina [JWT Debugger - jwt.lannysport.net](https://jwt.lannysport.net/)

- Ahora, segun el nombre y las pistas del desafio, me dieron el Codigo fuente porque adentro se olvidaron de borrar la llave secreta para encriptar el jwt
- cuando lo descargo y lo veo, miro montañas y montañas de carpetas con .java dentro y debo abrir cada uno de ellos para encontrar la llave despues de analizar el codigo...
![[Pasted image 20251008125010.png]]

- entonces mejor usaremos `john` en kali, como lo hicimos en **JaWT Scratchpad**
- abro kali, creo un .txt con el token adentro y uso el comando (los pasos antes de esto estan en el desafio anterior Jawt)
```
john token.txt -w=/usr/share/wordlists/rockyou.txt
```
- y me regresa que la clave es "1234"
![[Screenshot_2025-10-08_14_31_59.png]]
- ya con la clave voy a la pagina para desincreotar el jwt y pongo en la parte de abajo "1234"
- en la de en medio tengo que cambiar role por admin y usedID por 2
![[Pasted image 20251008125711.png]]
- ahora copio mi nuevo JWT y regreso a la pagina
- en local storage doy click derecho sobre "auth-token" y pongo "edit key"
- copio mi nueva llave donde esta la anterior y en "token-payload" modifico igual role y userID por Admin y 2 respectivamente
- Al darle actualizar en los elementos y despues en la pagina me dan la bandera: **picoCTF{w34k_jwt_n0t_g00d_7745dc02}**
## Notas
- viendo el writeup que estaba siguiendo ya sabia que la llave era 1234 y que la consiguio revisando todo el src, pero yo no queria revisar todo solo para encontrarlo y por eso mejor se me ocurrio usar `john` para mas rapido y funciono

## Referencias
[Java Code Analysis picoCTF 2023. This medium-level Web Exploitation is… | by Zarar Ahmed | Medium](https://zarrarkolachi.medium.com/java-code-analysis-picoctf-2023-e4ab29d4743e)