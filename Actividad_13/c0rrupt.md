
## Reto
### c0rrupt

## Descripcion
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.

## Solucion
- al descargar el archivo tenemos `mystery` sin extencion y si tratamos de hacerle un file solo nos dice que es data
- vemos entonces sus primeros bits en hexdump con `xxd mystery | head` y observamos esto:
```
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
  
```
- no podemos ver ninguna firma especifia entonces hay que buscar por sus bits
- utilizando esta pagina([List of file signatures - Wikipedia](https://en.wikipedia.org/wiki/List_of_file_signatures)) buscamos por "89" y vemos que es el mas parecido
```
|`89 50 4E 47 0D 0A 1A 0A`|`‰PNG␍␊␚␊`|
```
- entonces hay que arreglar esto usando `hexeditor mystery`
- abrimos el editor y doy en Actions->Find...(Cntrl+Shift+F) para buscar por hex bytes y busco "89 65 4e 34" (nota: si hay mas de un espacio entre bites se tiene que poner tambien todos los espacios)
- cuando lo encuentro lo cambio por el que encontre en la lista de firmas
- despues no entendi nada de lo que se estaba haciendo en los writeups y solo hice los cambios que encontre en discord:
```
- corregir IHDR : 43 22 44 52 por 49 48 44 52

- corregimos `pHys`, cambiamos `aa 00 16 25 00 00 16 25` por `00 00 16 25 00 00 16 25`
- corregimos el tamaño del chunk, cambiamos `AA AA FF A5` por `00 00 FF A5`
- corregir chunk anterior para que diga `IDAT` , cambiamos `AB 44 45 54` por `49 44 41 54`
```
- al final lo guardo y abro la imagen que quedo y obtengo la bandera: **picoCTF{c0rrupt10n_1847995}**
## Notas

## Referencias
[List of file signatures - Wikipedia](https://en.wikipedia.org/wiki/List_of_file_signatures)
[picoCTF 2021 writeup [21] - Forensic - c0rrupt - YouTube](https://www.youtube.com/watch?v=7zY4VkiWbBI&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=21)
[picoCTF -‘c0rrupt’ walkthrough. Hello People, In this write up I have… | by MsProg | Medium](https://medium.com/@mohammedsbihi11/picoctf-c0rrupt-walkthrough-9b40ac5b1ccc)
[picoCTF 2019 - [Forensic] c0rrupted (250 points) - HackMD](https://hackmd.io/@FlsYpINbRKixPQQVbh98kw/Bk9Wj63vH)