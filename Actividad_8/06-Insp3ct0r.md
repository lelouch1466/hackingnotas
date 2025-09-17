
## Reto
Insp3ct0r

## Descripcion

Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/44924/` ([link](https://jupiter.challenges.picoctf.org/problem/44924/)) or http://jupiter.challenges.picoctf.org:4492
## Solucion
- Al buscar en los elementos de la pagina con un `Ctrl+Shift+C` encuentro esto:
	- <!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
- Buscando en el CSS con un click derecho encuentro:
	- /* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
- Y finalmente en el Javascript encuentro:
	- /* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?f10be399} */
- Poniedo las partes juntas me da la bandera: **picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?f10be399} **

## Notas


<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?f10be399} */

## Referencias
