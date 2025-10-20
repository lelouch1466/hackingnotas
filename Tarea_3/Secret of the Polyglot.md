
## Reto
### Secret of the Polyglot
## Descripcion
The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/8/flag2of2-final.pdf).
## Solucion
- descargamos el archivo que nos dan pero tiene algo raro
- se llama algo asi como "bandera_2of2.pdf"
- si lo abrimos vemos que es la segunda parte de la bandera *1n_pn9_&_pdf_249d05c0}* pero nos falta la primera parte
- trate de cambiar el link que nos da para descargarlo poniendo el "10f2" pero no
- trate de ver los metadatos o tratar de hacerle un `unzip` pero nada
- cuando le hice un `file` me salio que era un png, lo cual se me hizo raro porque temina en .pdf y se abre como un pdf
- hice una copia cambiando su extencion
```
cp flag2of2-final.pdf flag1.png   
```
- y al abrir la copia, era la primera parte, lo que me dio la bandera completa: **picoCTF{f1u3n7_1n_pn9_&_pdf_249d05c0}**



## Notas
- no se como funciona esto pero esta chido saber que es posible
## Referencias
