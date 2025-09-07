## Reto
convertme.py

## Descripcion
Run the Python script and convert the given number from decimal to binary to get the flag.[Download Python script](https://artifacts.picoctf.net/c/23/convertme.py)

## Solucion
- Despues de descargar el archivo vemos que es un .py
- Como vi en el desafio codebook, lo corro usando `python3 convertme.py`
- me pregunta un numero en base decimal y que se lo tradusca a base binario, usando cybershef convierto el numero y me regresa mi bandera: **picoCTF{4ll_y0ur_b4535_9c3b7d4d}**

## Notas
- Tambien intente usar un strings sobre el archivo y veo que esta la bandera codificada en hex en el codigo, pero al tratar de decodificarla desde fuera de la aplicacion solo me dio caracteres random

## Referencias
[From Decimal, To Binary - CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Decimal\('Space',false\)To_Binary\('Space',8\)&input=MjA)