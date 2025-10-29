
## Reto
### HideToSee
## Descripcion
How about some hide and seek heh?Look at this image [here](https://artifacts.picoctf.net/c/238/atbash.jpg).
## Solucion
- al ver la imagen que nos dan solo nos muestra una forma de sifrado llamado atbash
- no veo la bandera por ningun lado, trato de metadatos con `exiftool` pero nada
- por la pista que nos dan que dice que trate de extraer la imagen trato entonces `unzip` a la imagen pero nada
- pienso entonces en esteganografia y busco en mis notas de como sacar informacion secreta de JPG y encuentro el `steghide` 
- hago:
```
steghide info atbash.jpg
```
- y encuentro que efectivamente tiene un archivo embedido dentro de la imagen y que no hay passphrase
```
"atbash.jpg":
  format: jpeg
  capacity: 2.4 KB
Try to get information about embedded data ? (y/n) y
Enter passphrase: 
  embedded file "encrypted.txt":
    size: 31.0 Byte
    encrypted: rijndael-128, cbc
    compressed: yes

```
- para extraerlo debo hacer esto:
```
steghide extract -sf atbash.jpg
```
- lo cual extrae encrypted.txt (cuando me pregunta por passphrase solo le doy enter ya que no tiene)
- dentro tiene este texto: `krxlXGU{zgyzhs_xizxp_8z0uvwwx}` pero como la imagen es del cifrado de atbash, lo pongo en cybershef y me regresa la bandera: **picoCTF{atbash_crack_8a0feddc}**
## Notas

## Referencias
[picoCTF — HideToSee. For the challenge we need to download a… | by Tommy S | Medium](https://medium.com/@1nfus3/picoctf-hidetosee-4d44a3acdf5c)