
## Reto
picobrowser

## Descripcion
This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/28921/` ([link](https://jupiter.challenges.picoctf.org/problem/28921/)) or http://jupiter.challenges.picoctf.org:28921

## Solucion
- al entrar a la pagina no me aparece nada porque no estoy en picobrowser
- pongo esto en consola para que me de los elementos de la web como si fuera picobrowser:
	- `curl https://jupiter.challenges.picoctf.org/problem/28921/flag -H "User-Agent:picobrowser"`
- al buscar un poco encuentro:  `<code>picoCTF{p1c0_s3cr3t_ag3nt_84f9c865}</code>`

ALT:
- Se puede con una extencion para mandar en que navegador estoy

## Notas
- el servidaor sabe que navegador uso pero al igual que la cockies, se puede cambiar que le enviamos al servidor desde consola

## Referencias
