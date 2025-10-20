
## Reto
### waves over lambda
## Descripcion
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 13758`.
## Solucion
- al entrar al netcat nos da un texto que parece estar cifrado
- pero, si volvemos a conectarnos vemos que el texto cambia cada vez que nos conectamos
- esto nos dice que no tiene un cifrado fijo y que es mas random
- parece que solo toma una letra y la sustituye por otra random
- buscamos por substitution solver en linea
- cuando le damos el mensaje, lo rompe y nos da la bandera: **frequency_is_c_over_lambda_dnvtfrtayu**
## Notas

## Referencias
[Substitution Solver | guballa.de](https://www.guballa.de/substitution-solver)