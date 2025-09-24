
## Reto
JaWT Scratchpad

## Descripcion
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/63090/` or http://jupiter.challenges.picoctf.org:63090
## Solucion
- al entrar a la pagina nos dice que entremos con cualquier nombre excepto admin
- si intentamos entrar con admin nos rechaza, asi que entramos con el nombre de juan
- se genera un token con jwt que se guarda en las cookies
- guardamos el token encriptado y lo ponemos en un debugger para que nos de las 3 partes del jwt![[Pasted image 20250924114627.png]]

  <img width="1604" height="764" alt="Pasted image 20250924114627" src="https://github.com/user-attachments/assets/e26e9c7e-ceff-4fbe-b156-4cba0b24ae26" />

- al tratar de cambiar el usuario de juan a admin en la parte derecha nos cambia el ecriptado pero al tratar de usarlo en la pagina esto no funciona; esto porque no la firma de verificacion no es correcta
- para poder encontrar la forma usare kali que tiene los comandos necesarios para esto
- dentro de kali voy hasta `/usr/share/wordlists/rockyou.txt.gz` que es una lista de las palabras mas usadas para encryptar, pero para usarla primero tengo que hacer esto: `gizip -d /usr/share/wordlists/rockyou.txt.gz`
- Ahora creo un .txt y pongo dentro el jwt encriptado
- ahora uso el comando `john token -w=/usr/share/wordlists/rockyou.txt
- Esto me regresa la firma que se uso para encriptarlo, la cual fue: *ilovepico*
- ahora pongo eso en la parte de abajo del debugger y cambio el user a admin, esto me regresa un encriptado que si servira y al guardarlo en mis cookies con cookie editor y recargar la pagina puedo entrar a admin y encuentro la bandera: **picoCTF{jawt_was_just_what_you_thought_f859ab2f}**


## Notas
- `john` es el comando para usar john the ripper, una herramienta para encontrar constraseñas debiles de usuarios

## Referencias
[JSON Web Token Introduction - jwt.io](https://www.jwt.io/introduction#what-is-json-web-token-structure)
[JWT Debugger - jwt.lannysport.net](https://jwt.lannysport.net/)
