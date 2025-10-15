
## Reto
webnet0
## Descripcion
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.

## Solucion
- el archivo que nos dan es un .pcap, entonces uso wireshark para abrirlo
- no puedo ver nada interesante en las lineas ni buscando ni siguiendo porque estan en TSL(transport layer security), un protocolo de privacidad
- como tambien me dieron la llave la agrego en : Edit -> preference -> RSA -> agregar llave
- cuando le doy en apply noto que una lineas cambiaron a verde y ahora son http
- si le doy follow a http, buscando un poco en lo que sale esta la badera **picoCTF{nongshim.shrimp.crackers}**

## Notas

## Referencias
[Webnet 0 & 1 — PicoCTF Writeup. Day 31 | by Eric H | Medium](https://medium.com/@erichdryn/webnet-0-1-picoctf-writeup-db9b1a4a825f)