
## Reto
### interencdec
## Descripcion
Can you get the real meaning from this file.Download the file [here](https://artifacts.picoctf.net/c_titan/2/enc_flag).

## Solucion
- nos dan con texto de ASCII:
```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==
```
- parece ser un texto en base64, cuando lo ponemos en cybershef nos da:
```
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzc4MjUwaG1qfQ=='  
```
- parece mas base64 pero no se traduce a nada asi como esta, como vemos comillas lo mas seguro es que solo lo que esta dentro es importante, cuando ponemos solo eso nos regresa algo:
```
wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}
```
- ya parece ser la bandera pero en algun ROT
- vamos haciendo rotaciones de 1 en 1 hasta que llegamos a la bandera en la rotacion 19: **picoCTF{caesar_d3cr9pt3d_78250afc}**

## Notas

## Referencias
