
## Reto
### Ph4nt0m 1ntrud3r
## Descripcion
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap) and try to get the flag.n

## Solucion
- al descargar el .pcap lo abrimos con wireshark en kali
- podemos ver que en la parte de la esquina donde se muestran los paquetes hay una parte que se ve parece ser base64
- pero son muchas lineas para ver cada una y aparte hay algunas que si lo desciframos no nos da texto legible
- viendo las pistas vemos que nos dice que debemos filtrar los paquete de alguna forma y que el tiempo tambien el clave
- viendo las paquetes vemos que los de largo 4 y 12 son los que sí contienen informacion importante entonces los filtramos asi:
```
tcp.len eq 12 || tcp.len eq 4
```
- como nos dicen que el tiempo es importante los acomodamos para que vallan del mas temprano al mas tarde dando click en time
- ahora vemos los paquetes de cada uno dando click derecho `segmented data` o con `Cntrl+Shift+O` 
- al poner todos los paquetes nos quedara esto:
```
cGljb0NURg==
ezF0X3c0cw==
bnRfdGg0dA==
XzM0c3lfdA==
YmhfNHJfOQ==
NTlmNTBkMw==
fQ==
```
- que al ponerlo en cybershef para base64 nos regresa la bandera: **picoCTF{1t_w4snt_th4t_34sy_tbh_4r_959f50d3}**
## Notas
- la bandera tiene razon, no fue facil

## Referencias
[picoCTF 2025 - [ Forensic ] - Ph4nt0m 1ntrud3r - YouTube](https://www.youtube.com/watch?v=_YKC5Smffeg)
