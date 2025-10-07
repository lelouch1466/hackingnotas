
## Reto
dont-you-love-banners

## Descripcion
Can you abuse the banner?The server has been leaking some crucial information on `tethys.picoctf.net 53135`. Use the leaked information to get to the server.To connect to the running application use `nc tethys.picoctf.net 63856`. From the above information abuse the machine and find the flag in the /root directory.

## Solucion
- nos dan 2 conexiones para ver
- si tratamos de entrar a la segunda nos aparece un "welcome" y nos pregunta por una contraseña
- si entramos a la segunda nos da la contraseña "My_Passw@rd_@1234"
- cuando la ponemos en la segunda conexion ahora nos pregunta por "la mejor conferencia de cyberseguridad en el mundo?"
  una busqueda rapida en google nos da 3 opciones: black hat, def con y rsa conference
- intentamos estas y la respuesta era "def con"
- ahora nos pregunta por el primer hacker que hizo phreaking(llamadas gratis por telefono), igualmente una busqueda rapida nos dice que fue "John Draper"
- cuando contestamos todo nos deja entrar al sistema de player@challenge
- si hacemos un ls vemos 2 cosas: el baner de "welcome" y un texto
- si abrimos el texto nos dice que miremos mas profundo
- primero intente ir a `cd /` y hacer un grep por pico pero se travo la conexion y tuve que volver a intentarlo
- ahora mejor reviso la raiz de usuario con `ls -la /root` y veo que hay 2 cosas importantes: **flag.txt y script.py**
- desaforyunadamente si tratamos de abrir flag.txt no tenemos los permisos necesarios para hacerlo y un sudo tampodo funciona
- pero si podemos abrir script.py y obtenemos esto
```
player@challenge:~$ cat /root/script.py  
cat /root/script.py  
  
import os  
import pty  
  
incorrect_ans_reply = "Lol, good try, try again and good luck\n"  
  
if __name__ == "__main__":  
try:  
with open("/home/player/banner", "r") as f:  
print(f.read())  
except:  
print("*********************************************")  
print("***************DEFAULT BANNER****************")  
print("*Please supply banner in /home/player/banner*")  
print("*********************************************")  
  
try:  
request = input("what is the password? \n").upper()  
while request:  
if request == 'MY_PASSW@RD_@1234':  
text = input("What is the top cyber security conference in the world?\n").upper()  
if text == 'DEFCON' or text == 'DEF CON':  
output = input(  
"the first hacker ever was known for phreaking(making free phone calls), who was it?\n").upper()  
if output == 'JOHN DRAPER' or output == 'JOHN THOMAS DRAPER' or output == 'JOHN' or output== 'DRAPER':  
scmd = 'su - player'  
pty.spawn(scmd.split(' '))  
  
else:  
print(incorrect_ans_reply)  
else:  
print(incorrect_ans_reply)  
else:  
print(incorrect_ans_reply)  
break  
  
except:  
KeyboardInterrupt
```
- vemos que el baner de "welcome" con el que empieza la conexion mo esta imprezo en el programa, si no que agarra el texto de "banner" en la pagina principal y lo imprime
- podemos abusar esto cambiando el contenido de "banner" pero como hacemos para que lea "flag.txt" desde /root
- usaremos un symlink que es solo un acceso directo a otro archivo
- primero borro el banner original con `rm banner` y ahora creo un acceso directo a flag.txt y lo llamo "banner" para que el programa lo lea como si fuera el original
```
ln -s /root/flag.txt banner
```
- ahora salgo de la conexion y vuelvo a entrar y ahora en ves de decir "welcome" me da la bandera: **picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_68ca8b23}**
![[Pasted image 20251005165722.png]]


## Notas

## Referencias
[picoCTF 2024: dont-you-love-banners | by Altair | Medium](https://medium.com/@niceselol/picoctf-2024-dont-you-love-banners-40b8c1fc5050)