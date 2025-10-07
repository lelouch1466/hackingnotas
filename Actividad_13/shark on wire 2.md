
## Reto
shark on wire 2
## Descripcion
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.

## Solucion
- abro el archivo capture.pcap en wireshark
- al revisar las lineas que hay no veo nada interesante porque ni se que estoy buscando
- hago lo mismo que en shark on wire, vou a una UDP y le doy en follow
- al ir cambiando de streams veo que en la 32 esta "start" y en 60 esta "end"
- La 32 y 60 tienen en comun que ambas van destinadas al puerto 22
- en el filtro escribo lo siguiente para filtrar las que esten en ese puerto
```
udp.port == 22
```
- reviso estas conexiones pero no se ve nada interesante
- pero se ve algo raro en la columna de "info", todas empiezan con 5+3digitos
- parece que los 3digitos que hay son de ASCII entonces copio cada uno de ellos y termino con lo siguiente
```
000 112 105 099 111 067 084 070 123 112 049 076 076 102 051 114 051 100 095 100 097 116 097 095 118 049 097 095 115 116 051 103 048 125 000

```
- Pongo esa cadena en este sitio:[Decimal to text: Decode Unicode code points to text - cryptii](https://cryptii.com/pipes/decimal-text) y obtengo la bandera: **picoCTF{p1LLf3r3d_data_v1a_st3g0}**
## Notas
- use mas el discord para encontrar la bandera que la referencia que encontre

## Referencias
[PicoCTF 2019 - shark on wire 2](https://zomry1.github.io/shark-on-wire-2/)

