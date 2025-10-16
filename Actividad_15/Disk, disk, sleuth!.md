
## Reto
Disk, disk, sleuth!
## Descripcion
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/a734f18939e0aaea9d27bc7a243a0ed0/dds1-alpine.flag.img.gz)
## Solucion
- descargamos la imagen de un disco
- aplicamos
```
srch_strings dds1-alpine.flag.img | grep pico
```
- y encontramos la badera

## Notas

## Referencias
