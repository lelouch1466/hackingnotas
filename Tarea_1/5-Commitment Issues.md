## Reto
Commitment Issues

## Descripcion
I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/136/challenge.zip)
## Solucion
- Al descomprimir el archivo el .py incluido solo es un texto que dice "TOP SECRET"
- Al aplicar un grep para buscar pico en la carpeta de git me mostro que a habiado 2 commits:
	- 87b85d7dfb839b077678611280fa023d76e017b8 picoCTF <ops@picoctf.com> 1710201977 +0000    commit (initial): create flag
	- 8dc51806c760dfdbb34b33a2008926d3d8e8ad49 picoCTF <ops@picoctf.com> 1710201977 +0000    commit: remove sensitive info
- Puedo ver que necesito revertir al primer commit para encontrar la bandera pero no se como hacerlo
- al ver la primera pista me dirije a la pagina del manual de git y ahi encuentro como revisar el primer commit con `git checkout <commit ID>`
- Al revisar los commits supongo que todos esos numeros son el ID de los commits entonces pongo `git checkout 87b85d7dfb839b077678611280fa023d76e017b8     `
- Esto me revierte al commit y al abrir el mensaje del principio obtengo la bandera: **picoCTF{s@n1t1z3_ea83ff2a}**

## Notas
- Antes de ver el manual en linea intente usan `man git` para encontrar algun comando para revertir commit, lo busque usando /commit en el manual.
  encontre git revert y al aplicarlo me salio error pero tambien una pistas pero no supe como seguir.


## Referencias
[The CTF Primer](https://primer.picoctf.org/#_git_version_control)