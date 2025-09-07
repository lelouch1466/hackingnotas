## Reto
Codebook

## Descripcion
Run the Python script `code.py` in the same directory as `codebook.txt`.

- [Download code.py](https://artifacts.picoctf.net/c/1/code.py)
- [Download codebook.txt](https://artifacts.picoctf.net/c/1/codebook.txt)

## Solucion
- Ambas carpetas las descargo en el mismo directorio, en este caso en root
- Despues trato de correr code.py pero no tiene permisos, se los doy con un `chmod +x code.py`
- Trato de correrlo con `./code.py` pero como estamos en linux no se corre un archivo de python
- Una busqueda rapida en google de como porrer un .py en linux me resulto en que debo correlo como `python3 [nombre de .py]` y al ejecurtalo me regresa la bandera: **picoCTF{c0d3b00k_455157_d9aa2df2}**

## Notas
- Ahora se como correr un .py en linux desde terminal

## Referencias
