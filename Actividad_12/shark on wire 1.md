
## Reto
shark on wire 1
## Descripcion
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.
## Solucion
- al descargar el archivo veo que es un .pcap
- esto es un archivo que tiene de datos capturados en paquete que se envian desde la red
- para poder leerlo uso wireshark en kali y lo abro
- me salen muchas lineas con paquetes, al dar click derecho pongo la opcion de follow para seguir las de protocolo UDP
- Al principio no salen mas que caracteres sin sentido, pero al cambiar de stream de 4 a 5 me aparece 'pico' repetido
- Al cambiar de stream de 5 a 6 me aparece la bandera: **picoCTF{StaT31355_636f6e6e}**

## Notas

## Referencias
[PCAP: Captura de paquetes, qué es y qué necesita saber](https://www-comparitech-com.translate.goog/net-admin/pcap-guide/?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc)
[picoCTF 2021 writeup [16] - Forensic - shark on wire 1](https://www.youtube.com/watch?v=q8cM4sY0izw&list=PLDo9DMLZyP6kTZ8Td37-LdbAx4-yNfHBl&index=16)