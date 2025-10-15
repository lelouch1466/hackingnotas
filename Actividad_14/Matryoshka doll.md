
## Reto
Matryoshka dolls
## Descripcion
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/1b70cffdd2f05427fff97d13c496963f/dolls.jpg)

## Solucion
- al archivo parece solo una imagen normal
- si le hacemos `exiftool` vemos que tiene bastante informacion, mas de lo normal
- le hacemos un `unzip` a la misma imagen y genera una carpeta
- al entrar a la carpeta hay otra imagen igual
- repetimos el proceso de aplicar unzip a las imagenes que se generan hasta que al final nos queda flag.txt  con nuestra bandera


## Notas

## Referencias
