## Reto
chrono

## Descripcion
How to automate tasks to run at intervals on linux servers?Use ssh to connect to this server:

```
Server: saturn.picoctf.net
Port: 59840
Username: picoplayer 
Password: ENAFb6zfzn
```

## Solucion
- Despues de conectarme al servidor trate un ls pero no hay nada
- busque como mostrar carpetas ocultas con ls y encontre ls -a, y aunque si me salieron opciones ninguna resulto prometedora
- Sin saber que hacer busque una solucion en internet y solo era aplicar un `cat /etc/chrontab` y aparecio la bandera: **picoCTF{Sch3DUL7NG_T45K3_L1NUX_1d781160}**

## Notas
- No estoy muy inverso en linux entonces sin pistas no pude haber encontrado la solucion
- Despues del desafio busque porque funciona esto:
	- chrontab es una utilidad en sistemas operativos unix que permite programar comandos para que corran automaticamente en tiempos especificos o intervalos
	- etc es el directorio principal que contiene los archivos de la configuracion del sistema y aplicaciones

## Referencias
[picoCTF 2023 Chrono](https://www.youtube.com/watch?v=K9H6i73ydMM)
