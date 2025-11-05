
## Reto
### Sleuthkit Apprentice
## Descripcion
Download this disk image and find the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/136/disk.flag.img.gz)
## Solucion
- descargamos el archimo que es una imagen de un disco
- le hacemos el gzip para descomprimirlo
- ahora un mmls para ver las particiones y donde empiezan
```

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000360447   0000153600   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000360448   0000614399   0000253952   Linux (0x83)
```
- ya que se donde empiezan puedo usar "fls" para ver los archivos dentro de un sistema
- busco con este comando
```
fls -o 360448 -r disk.flag.img | grep flag
```
- encotramos la bandera que dice esta en el archivo numero 2371
- aplicamos un icat para abrilo con:
```
icat  -o 360448 -r disk.flag.img 2371
```
- y obtenemos la bandera
## Notas

## Referencias

AddType application/x-httpd-php .png