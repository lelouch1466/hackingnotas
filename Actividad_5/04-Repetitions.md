## Reto
Repetitions

## Descripcion
Can you make sense of this file?Download the file [here](https://artifacts.picoctf.net/c/473/enc_flag).

## Solucion
- Por el nombre del desafio espero tener que decodificar multiples veces un texto que me den
- Despues de descargar y abrir el archivo me sale un texto con diferentes caracteres
- Pongo el texto dentro de cybershef pero no me da ninguna opcion de recomendacion
- Busco una solucion para ver en que codigo puede estar el mensaje
- Veo que una forma de identificar este codigo es que por el string de caracteres y el uso de = significa que esta en base64
- con esta informacion uso cybershef para decifrar el mismo codigo en base 64 6 veces seguidas y me da la bandera: **picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_dfe803c6}**
## Notas
- No se distinguir los lenguajes de codigo codificado aun, tengo que practicar para entender como se ven e identificarlos

## Referencias
[picoCTF writeup: repetitions. repetitions is an easy challenge in the… | by Omstaendlig | Medium](https://medium.com/@omstaendlig/picoctf-writeup-repetitions-e37aa158416d)
[From Base64 - CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Base64\('A-Za-z0-9%2B/%3D',true,false\)&input=Y0dsamIwTlVSbnRpWVhObE5qUmZiak56ZEROa1gyUnBZekJrSVc0NFgyUXdkMjVzTURSa00yUmZaR1psT0RBell6WjlDZz09Cg&ieol=CRLF&oeol=CRLF)




