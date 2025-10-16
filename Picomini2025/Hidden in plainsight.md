
## Reto
Hidden in plainsight

## Descripcion
You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag.Download the jpg image [here](https://challenge-files.picoctf.net/c_saffron_estate/984460cb7eebc16b2908f91210cb8dc4936c63cb6d28c9475fa38dc6a443d1d6/img.jpg).

## Solucion
- Al descargar la imagen trato de revisar la metada pero y veo que en comentario hay codigo en base64: `c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9`
- cuando lo tradusco ahora me aparece: `steghide:cEF6endvcmQ=`
- aun mas base64 pero tambien con la palabra "steghide"
- al traducir el nuevo codigo me sale: `pAzzword`
- primero busco que es steghide y encuentro que es una herramienta para codificar/decodificar con estenografia
- la instalo y busco en --help para ver como se usa
- veo que puede extraer y con -p se le pasa un passphrase para que decodifique con eso
- le pregunto al chatgpt como usarlo correctamente y uso el comando:
```
steghide extract -sf img.jpg -xf salida.bin -p "pAzzword"
```
- con esto se crea salida.bin, al hacerle un file veo que es texto ASCII y al abrirlo con cat obtengo la bandera: **picoCTF{h1dd3n_1n_1m4g3_2ac27d95}
**
## Notas

## Referencias
[steghide | Kali Linux Tools](https://www.kali.org/tools/steghide/)

