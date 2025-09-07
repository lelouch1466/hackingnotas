## Reto
Super ssh
## Descripcion
Using a Secure Shell (SSH) is going to be pretty important.Can you `ssh` as `ctf-player` to `titan.picoctf.net` at port `52021` to get the flag?You'll also need the password `1db87a14`. If asked, accept the fingerprint with `yes`.If your device doesn't have a shell, you can use: [https://webshell.picoctf.org](https://webshell.picoctf.org/)If you're not sure what a shell is, check out our Primer: [https://primer.picoctf.com/#_the_shell](https://primer.picoctf.com/#_the_shell)
## Solucion
- Despues de inicializar el reto me da los datos para conectarme a un ssh
- Tan solo corri el comando `ssh ctf-player@titan.picoctf.net -p 52021` y puse la contraseña que me dieron y me dio la bandera **picoCTF{s3cur3_c0nn3ct10n_45a48857}**

## Notas
- La solucion de este fue bastante simple ya que el reto 'useless' ya nos habia enseñaado como conectarse con ssh

## Referencias
