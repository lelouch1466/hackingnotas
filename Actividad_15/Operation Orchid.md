
## Reto

## Descripcion
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/212/disk.flag.img.gz)s
## Solucion
- descargamos el archivo y es una imagen de un disk
- lo descomprimimos con gzip y vemos las particiones:
```
      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
```
- despues listamos los archivos de las particiones con fls y buscamos algun flag que encontramos en la particion 411648 en el root
- si vamos a la carpeta de root vemos esto:
```
r/r 1875:       .ash_history
r/r * 1876(realloc):    flag.txt
r/r 1782:       flag.txt.enc
```
- esta el historial de comandos, la bandera que no podemos ver y la bandera cifrada
- si vemos el historial vemos esto:
```
touch flag.txt
nano flag.txt 
apk get nano
apk --help
apk add nano
nano flag.txt 
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
```
- vemos que proceso sigui para cifrarla, entonces podemos descifrarla siguiendo el proceso en reverso
- primero copiamos la bandera cifrada en nuestro sistema local con:
```
icat -o 411648  disk.flag.img 1782 > flag.txt.enc  
```
- ahora para el contrario para descifrarla:
```
openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
```
- nos genera un flag.txt con la bandera adentro: **picoCTF{h4un71ng_p457_0a710765}**
## Notas

## Referencias


lelouch1466-picoctf@webshell:/tmp$ fls -o 411648 disk.flag.img 476
lelouch1466-picoctf@webshell:/tmp$ fls -o 411648 disk.flag.img 476 
lelouch1466-picoctf@webshell:/tmp$ fls -o 411648 disk.flag.img 2041
lelouch1466-picoctf@webshell:/tmp$ fls -o 411648 disk.flag.img 472
r/r 1875:       .ash_history
r/r * 1876(realloc):    flag.txt
r/r 1782:       flag.txt.enc
lelouch1466-picoctf@webshell:/tmp$ fls -o 411648 disk.flag.img 1857
Error extracting file from image (ext2fs_dir_open_meta: Error reading directory contents: 1857
)
lelouch1466-picoctf@webshell:/tmp$ fls -o 411648 disk.flag.img 1875
Error extracting file from image (ext2fs_dir_open_meta: Error reading directory contents: 1875
)
lelouch1466-picoctf@webshell:/tmp$ icat -o 411648 disk.flag.img 1875
touch flag.txt
nano flag.txt 
apk get nano
apk --help
apk add nano
nano flag.txt 
openssl
openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
shred -u flag.txt
ls -al
halt
lelouch1466-picoctf@webshell:/tmp$ icat -o 411648  disk.flag.img 1782 > flag.txt.enc                                 
lelouch1466-picoctf@webshell:/tmp$ ls
disk.flag.img  disk0.flag.img  flag.txt.enc  hsperfdata_root  node-compile-cache
lelouch1466-picoctf@webshell:/tmp$ openssl aes256 -salt -d -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
80EB09B51A7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:124:
lelouch1466-picoctf@webshell:/tmp$ ls
disk.flag.img  disk0.flag.img  flag.txt  flag.txt.enc  hsperfdata_root  node-compile-cache
lelouch1466-picoctf@webshell:/tmp$ cat flag.txt

