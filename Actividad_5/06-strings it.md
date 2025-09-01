## Reto
strings it
## Descripcion
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings) without running it?

## Solucion
- Despues de descargar el archivo, la pista me dice que corra el archivo usando `strings`
- Al correrlo me salen muchas lineas como: 
	s2296
	s4178
	s4139
	s4674
	...
- Como impreme demasiado es imposible encontrar la bandera
- Uso una tuberia con grep para buscarlo con el siguiente comando: `strings strings | grep 'pico'` y obtengo la bandera **picoCTF{5tRIng5_1T_827aee91}**

## Notas
- El uso de tuberia para este desafio fue gracias al desafio anterior Plumbing
- Aunque me dieron el link del tutorial de uso de strings, mejor use --help para entender como funciona

## Referencias
[strings(1) - Linux man page](https://linux.die.net/man/1/strings)