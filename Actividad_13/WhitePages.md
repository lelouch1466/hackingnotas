
## Reto
WhitePages
## Descripcion
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://jupiter.challenges.picoctf.org/static/74274b96fe966126a1953c80762af80d/whitepages.txt) is all blank!

## Solucion
- cuando abrimos el archivo no tiene nada
- si le damos un file dice que es un unicode
- si revisamos el hexdump vemos que tiene una cadena "e2 80 83" y a veces lo rompe un "20"
```
xxd -g 1 -l 100 whitepages.txt
```
- lo podemos interpretar como "e28082=1" y "20=0" y cambiamos eso con este comando:
```
sed 's/\xe2\x80\x83/0/g' whitepages.txt | sed 's/\x20/1/g'
```
- nos queda un texto en binario que si lo ponemos en cybershef nos da la bandera: **picoCTF{not_all_spaces_are_created_equal_c54f27cd05c2189f8147cc6f5deb2e56}**
## Notas

## Referencias
