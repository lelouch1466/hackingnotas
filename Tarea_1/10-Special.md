## Reto
Special (week)
![[Pasted image 20250906203823.png]]
## Descripcion
Don't power users get tired of making spelling mistakes in the shell? Not anymore! Enter Special, the Spell Checked Interface for Affecting Linux. Now, every word is properly spelled and capitalized... automatically and behind-the-scenes! Be the first to test Special in beta, and feel free to tell us all about how Special streamlines every development process that you face. When your co-workers see your amazing shell interface, just tell them: That's Special (TM)Start your instance to see connection details.

Additional details will be available after launching your challenge instance.
## Solucion
- Cuando me conecto al servidor se empieza a correr un programa que hace que todos lo que escriba lo ponga con mayusculas la primera letra
- Esto me impide escribir comandos en la consola y estoy atorado, la pista dice que trate diferentes sintaxis de shell pero no entiendo a que se refiera
- Busco una solucion y veo que hay formas diferentes para poner comandos en consola
- Uso `$parameter:=[comando]` para empezar a hacer comandos, primero aplico ls y veo que hay algo llamado *blargh*
- Trato de hacerle cat pero me dice que es un directorio, trato de hacerle cd pero por alguna razon cd no funciona
- Como no puedo moverme a la carpeta, la veo desde fuera con `$parameter:=ls blargh` y veo que ahi esta flag.txt, finalmente la abro con  `$parameter:=cat blargh/flag.txt` y obtengo la bandera: **picoCTF{5p311ch3ck_15_7h3_w0r57_f906e25a}**

## Notas
- Con estas practicas estoy aprendiendo como se usa linux mejor porque no sabia nada de esto

## Referencias
[PicoCTF Special](https://www.youtube.com/watch?v=LMZpHXgidrM)
