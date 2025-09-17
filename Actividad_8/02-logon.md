
## Reto
logon

## Descripcion
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/15796/` ([link](https://jupiter.challenges.picoctf.org/problem/15796/)) or http://jupiter.challenges.picoctf.org:15796

## Solucion
- Con la pista me logeo poniendo cualquier cosa  de usuario y cualquier contraseña pero no hay bandera
- No hay bandera en los elementos tampoco
- Me instalo un editor de coockies y vuelvo a entrar con cualquier usuario
- Otraa vez dentro ahora abro mi editor de coockies y veo que tengo el permiso de admin con "False", lo cambio a "True" y recargo la pagina y me dio la bandera **picoCTF{th3_c0nsp1r4cy_l1v3s_6edb3f5f}**

ALT:
- En consola:
	- curl -s -X GET https://jupiter.challenges.picoctf.org/problem/15796/flag -H "Cookie: username=admin; password=admin; admin=True" | grep pico

## Notas
- las coockies son pequeños archivos de texto que recuerdan informacion sobre tu visita a una web
- Se puede conseguir con GET
- POST para algo, no se :v

## Referencias
