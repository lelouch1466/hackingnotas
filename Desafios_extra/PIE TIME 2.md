
## Reto
### PIE TIME 2
## Descripcion
Can you try to get the flag? I'm not revealing anything anymore!!

Additional details will be available after launching your challenge instance.
## Solucion
- parecido al reto PIE TIME, nos dan el codigo fuente y el binario del programa y un netcat al cual conectarnos
- cuando nos conectamos nos pide nuestro nombre, nos repite nuestro nombre y despues nos pide una direccion para correr
![](../Imagenes/Pasted%20image%2020251029222121.png)
- tenemos que hallar la forma de explotar el programa para que nos de la direccion de main
- lo primero que se me ocurrio fue hacer overflow en la entrada de nombre para yo darle el comando como mi nombre despues de cierto numero de caracteres
- aunque esa no fue la solucion, si me llevo a ella, ya que el input no esta curado por lo que puedo poner cualquier cosa de nombre
- regrese a PIE TIME para revisar la linea de codigo que imprime la direccion de main y encontre esta linea:
```
printf("Address of main: %p\n", &main);
```
- cuando puse eso como mi nombre si me regreso una direccion...pero no era la de main
- fue aqui cuando me trabe y ya tube que ver una guia
- resulta que "%p" nos imprime la direccion de una lista de cosas, la primera para ser mas especifico
- entonces si le pasamos "%p %p" nos imprime las primeras 2 cosas y asi si ponemos mas
- entonces corremos el programa que nos dieron "vuln"(el binario) con gdb.
- pero primero, que es gdb????
---
### ¿Qué es `gdb`?

`gdb` (GNU Debugger) es el depurador estándar en Linux. Te permite ejecutar un programa paso a paso, inspeccionar memoria/variables/registros, poner _breakpoints_ (puntos de detención), ver la pila, desensamblar funciones y —en general— entender (y manipular) lo que hace un binario en tiempo de ejecución. Es imprescindible para depurar errores, entender exploits y analizar binarios.

### Qué puedes hacer con `gdb` (resumen rápido)

- Ejecutar el programa y detenerlo en `main` o donde quieras.
- Ver direcciones de funciones en la ejecución actual.
- Leer/escribir memoria y registros.
- Llamar funciones dentro del proceso (útil para probar `win()` desde gdb).
- Desensamblar una función para ver instrucciones máquina.
- Inspeccionar la pila y argumentos para explotar o analizar vulnerabilidades (por ejemplo, format string).
- Adjuntarte a un proceso en ejecución.
---

- entonces tratamos de correr:
```
gdb ./vuln
```
- al principio no me dejo y tuve que darle primero los permisos con:
```
chmod a+x vuln
```
- ya una vez que lo corre hacemos lo mismo que cuando estamos conectados al netcat
- cuando nos pregunta nuestro nombre ponemos tantas veces "%p" como nos deje, en este caso fueron 25
![](../Imagenes/Pasted%20image%2020251029223808.png)
- ahora como vemos nos dio la direccion de 25 cosas en orden de como aparecen
- la razon del porque estamos usando gdb para esto es para guardar esas salidas
- usamos el siguiente comando para que nos muestre la lista de estas salidas:
```
x/25gx $rsp
```
![](../Imagenes/Pasted%20image%2020251029224121.png)
- ahora con el siguiente comando podemos verificar a que pertenece cada direccion
```
x/gx <address>
```
- checamos de una en una y en la 25 encontramos que esa es main
![](../Imagenes/Pasted%20image%2020251029224411.png)
- pero lo estamos corriendo de manera local, de que nos sirve saber la direccion aqui?
- lo que nos importa no es la direccion, si no la posicion de la direcion
- incluso si con PIE cambia la direccion cada vez que se corre el programa, la posicion en la lista de direcciones no cambia y se mantiene igual
- esto quiere decir que si le decimos al programa que imprima la direccion 25 de la lista, esta nos regresara la posicion de main
- para eso cuando nos pida nuestro nombre le diremos que imprima `%25$p`
- antes de volver a conectarnos checamos por la diferencia de bits entre main y win en el binario
```
lelouch1466-picoctf@webshell:~$ readelf -s vuln | egrep '\b(main|win)\b'
    69: 000000000000136a   150 FUNC    GLOBAL DEFAULT   16 win
    73: 0000000000001400    72 FUNC    GLOBAL DEFAULT   16 main
```
- nos conectamos al netcat y ponemos `main en: %25$p`
- nos regresa la direccion de main y le digo al chat que con esa direccion y la diferencia de bits me regrese donde esta win
- ponemos la direccion calculada y me da la bandera: **picoCTF{p13_5h0u1dn'7_134k_cdbb451d}**
![](../Imagenes/Pasted%20image%2020251029225604.png)
## Notas

## Referencias
[picoCTF 2025: PIE TIME 2](https://blog.cbarkr.com/ctf/picoCTF/practice/PIE-TIME-2)