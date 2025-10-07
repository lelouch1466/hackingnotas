
## Reto
flag-shop
## Descripcion
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/253c4651d852ac6342752ff222cf2a83/store.c). Connect with `nc jupiter.challenges.picoctf.org 9745`.
## Solucion
- una vez dentro del sistema puedo checar mi balance, compar baderas o salir
- mi balance esta fixeado a 1100 y no hay forma de subirlo normalmente
- revisando el codigo veo que cuando se compra un bandera de 900 se hace un calculo con ints para ver cuanto seria el total
- un int soporta hasta el numero **2147483647** y si lo dividimos entre 900 nos da ***2,386,092** que es el maximo numero de banderas al que puede llegar la cuenta
- si pongo un algo que exceda ese numero la cuenta se hara negativa y hara que mi balance se incremente (balance - (-cuenta)), pero si pongo un numero demasiado grande no pasa nada
- 2400000 y esto hace la cuenta negativa y me da el balance necesario para comprar la bandera: **picoCTF{m0n3y_bag5_65d67a74}**

## Notas
- si pense que la solucion iba a ser una corrupcion de varible con overflow o hacer que la cuenta fuera negativa pero no supe que cantidad poner para eso

## Referencias
[PICO CTF — flag_shop. 08/02/24 — flag_shop | by Banana Eliptical | Medium](https://medium.com/@lukaskenderoski/pico-ctf-flag-shop-e643f53d9642)