
## Reto
Mind your Ps and Qs

## Descripcion
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/2604f8b51a5cc62d38a3736938f19cef/values)
## Solucion
- al descargar el archivo y abrirlo nos dan estos valores
```
c: 861270243527190895777142537838333832920579264010533029282104230006461420086153423
n: 1311097532562595991877980619849724606784164430105441327897358800116889057763413423
e: 65537
```
- necesito obtener p y q pero solo tengo n
- puedo hacerlo de 2 formas
- uso algun facorizador de primos en linea para sacar los factores de p
- pongo los valores en [RSA Cipher Calculator - Online Decoder, Encoder, Translator](https://www.dcode.fr/rsa-cipher) y me da la bandera directamente: **picoCTF{sma11_N_n0_g0od_13686679}**
## Notas
- en rsa tener un valor de n pequeño es malo porque es facil calcular los primos que lo conforman, lo cual nos da p y q y podemos descifrarlo
## Referencias
[Mind your Ps and Qs](https://gist.github.com/nick3499/54c8030c2170116526d06de3e0c94aec)

[RSA Cipher Calculator - Online Decoder, Encoder, Translator](https://www.dcode.fr/rsa-cipher)