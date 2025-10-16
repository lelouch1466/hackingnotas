
## Reto
### Crack the Gate 2
## Descripcion
The login system has been upgraded with a basic rate-limiting mechanism that locks out repeated failed attempts from the same source. We’ve received a tip that the system might still trust user-controlled headers. Your objective is to bypass the rate-limiting restriction and log in using the known email address: **ctf-player@picoctf.org** and uncover the hidden secret.

Additional details will be available after launching your challenge instance.
## Solucion
- al iniciar el reto nos dan la pagina y una lista de posibles contraseñas para el usuario que tambien nos dan
- al entrar a la pagina vemos que es muy parecido al de crack the gate 1 pero esta vez no tenemos X-dev-acces
- peor aun, si intentamos de 1 vez y estamos mal ya no nos vuelve a dejar intentar dentro de 20 minutos
- Tenemos que encontrar una forma de sobrepasar el limite para intentr todas las 20 contraseñas

- Uso burpsuite para lograr esto, al momento de mandar el request desde burpsuite le doy en la pagina de proxy->intercept on
- una vez que obtengo el request lo mando al Intruder
- desde el intruder veo que en el HEADER de la pagina no hay nada que le diga precisamente el origen del request entonces debe tomarlo automaticamente de alguna parte
- viendo la descripcion del programa dice que "puede que el sistema siga aceptando HEADERS controlados por usuario" y viendo la pista tal parece que debo usar `X-forwarded-for`

- X-Forwarded-For se utiliza en el header para mandar la ip en el request
- **Justo debajo de Host** agrego `X-Forwarded-For: 127.0.0.1` 
- como voy a necesitar 2 tipos de payloads (1 para ips y otro para las contraseñas)
- en vez de poner `sniper atack` pongo `Pitchfork atack` 
- ya tengo la lista de contraseñas entonces le pido al chat una lista de ip y obtengo esto:
```
127.0.0.1
192.168.1.100
10.0.0.5
172.16.0.10
100.64.0.1
169.254.1.1
8.8.8.8
1.1.1.1
203.0.113.45
198.51.100.23
192.0.2.99
54.23.12.34
35.186.219.10
104.16.132.229
185.199.108.153
13.35.10.20
93.184.216.34
10.10.10.10
203.0.113.45, 198.51.100.23
10.0.0.5, 127.0.0.1
```
- las pongo en un ip.txt
- selecciono ambas partes que van a llevar payload y le doy en `Add` para que quede algo asi:
```
X-Forwarded-For: $127.0.0.1$
"password":"$lol$"
```
- ahora cuando selecciono cada set me pregunto por su payload unico, le doy en load y cargo ip.txt y passwords.txt respectivamente
- ahora empiezo el ataque, voy revisando cada una y veo que esta funcionando porque cuando detecta la misma ip me ponia:
```
{"success":false,
"error":"Too many failed attempts. Please try again in 20 minutes."
```
- y ahora solo me da "success: false" en mis ataques
- en cierto request veo que paso el ataque y obtengo la bandera: **picoCTF{xff_byp4ss_brut3_3477bf15}**
![[Screenshot_2025-10-08_18_11_14 2.png]]

## Notas
- batalle mucho al principio porque no sabia si estaba poniendo bien el add en burpsuite y no sabia como darle payload diferente a cada set
- despues pense que lo que tenia que cambiar era el User-agent pero solo me daba errores en el ataque y por alguna razon siempre tardaban mucho los ataques, como 30 segundos cada linea
- fue hasta que vi las pistas que me di cuenta que tenia que usar X-forwarded
- incluso sabiendo que eso era lo que tenia que usar, cuando lo puse en mi header seguia sin servir 
- antes de pedirle la lista al chatgpt trte de avanzar el ip cada 10 pero no servia
- fue hasta que puse el X-Fowarded justo debajo del Host y use la lista de ips que todo por fin sirvio
- Incluso ya cuando sirvio, hay algunas IPs de la lista en la parte de abajo que no sirvieron por ser mas de 1 intento

## Referencias
