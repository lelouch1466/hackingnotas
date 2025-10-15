
## Reto
WebNet1

## Descripcion
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.

## Solucion
- como nos dan un .pcap y una llave haremos lo mismo que en webnet0
- abrimos el .pcap en wireshark y ponemos la llave en RSA
- nos aparecen lineas verdes en HTTP y la seguimos
- si en la parte de abajo en "find" ponemos pico despues de unos cuantas busquedas encontramos la bandera: **picoCTF{honey.roasted.peanuts}**
## Notas

## Referencias
[Webnet 0 & 1 — PicoCTF Writeup. Day 31 | by Eric H | Medium](https://medium.com/@erichdryn/webnet-0-1-picoctf-writeup-db9b1a4a825f)