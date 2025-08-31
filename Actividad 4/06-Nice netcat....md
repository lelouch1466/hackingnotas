## Reto
 Nice netcat...

## Descripcion
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 22902`, but it doesn't speak English...

## Solucion
- Al poner el comando en la terminal nos dan bastantes numeros de esta forma:
				112 
				105 
				99 
				111 
				...
- Es un codigo en decimal, lo puse en cyberchef y para no estar decifrando de 1 en 1 puse en la receta que el delimitador sea un salto de linea.
- Al final me dio la bandera: **picoCTF{g00d_k1tty!_n1c3_k1tty!_d3dfd6df}
**

## Notas
- Ahora se como delimitar en cibershef para mayor eficiencia al decifrar codigos.

## Referencias
[From Decimal - CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Decimal\('Line%20feed',false\)&input=MTEyIA0KMTA1IA0KOTkgDQoxMTEgDQo2NyANCjg0IA0KNzAgDQoxMjMgDQoxMDMgDQo0OCANCjQ4IA0KMTAwIA0KOTUgDQoxMDcgDQo0OSANCjExNiANCjExNiANCjEyMSANCjMzIA0KOTUgDQoxMTAgDQo0OSANCjk5IA0KNTEgDQo5NSANCjEwNyANCjQ5IA0KMTE2IA0KMTE2IA0KMTIxIA0KMzMgDQo5NSANCjEwMCANCjUxIA0KMTAwIA0KMTAyIA0KMTAwIA0KNTQgDQoxMDAgDQoxMDIgDQoxMjUgDQoxMA&ieol=CRLF)