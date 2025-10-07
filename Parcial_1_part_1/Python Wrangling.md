
## Reto
### Python Wrangling

## Descripcion
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/ende.py) using [this password](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/pw.txt) to get [the flag](https://mercury.picoctf.net/static/0bf545252b5120845e3b568b9ad0277e/flag.txt.en)?

## Solucion
- descargamos el script, la contraseña y la bandera
- al tratar de correr el programa con `python3 ende.py` nos dice que le faltan argumentos:
```
usage: ende.py (-e/-d) [file]
```
- intuyo que -d es decifrar y -e es enconde
- entonces lo corro como `python3 ende.py -d flag.txt`
- al correrlo me pide una contraseña que esta dentro del .txt de contraseña que descargamos y lo corre y nos da la bandera: **picoCTF{4p0110_1n_7h3_h0us3_6008014f}**
## Notas

## Referencias
