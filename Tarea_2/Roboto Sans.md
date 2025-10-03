
## Reto
Roboto Sans

## Descripcion
The flag is somewhere on this web application not necessarily on the website. Find it.Check [this](http://saturn.picoctf.net:61362/) out.

## Solucion
- al abrir la pagina se ve muy normal todo y ni al inspeccionar los elementos se ve algo
- por el nombre del desafio busco en el [link]/robots.txt y veo estas tres lineas
```
ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
```
- al decifrar la segunda linea de base64 me da *js/myfile.txt*
- al ponerlo [link]/js/myfile.txt me da la bandera **picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}**
## Notas

## Referencias
