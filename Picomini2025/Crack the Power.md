
## Reto
### Crack the Power

## Descripcion
We received an encrypted message. The modulus is built from primes large enough that factoring them isn’t an option, at least not today. See if you can make sense of the numbers and reveal the flag.Download the [message](https://challenge-files.picoctf.net/c_amiable_citadel/e94b75043f1b053af9913af9f600a9379bc34562c82e7c4fa1796440beef950f/message.txt).
## Solucion
- al descargar el archivo veo que tiene 3 variables con un buen de numeros cada uno, n, e y c
- e es solo 20 mientras que los otros son grandes, por la pistas esto indica que es coppersmith_atack
- tal parece que tengo que realizar la raiz e de c, para eso necesito usar gympy2 de pyhton
- le pido a chatgpt que me haga un codigo para resolver la raiz e de c y que me lo imprima en texto y me devuelve esto:
```
  GNU nano 6.2                                                                                                  pls_funciona.py *                                                                                                         
import gmpy2
from gmpy2 import mpz

n = mpz(553804...)
e = 20
c = mpz(6406374308104...)

# Sacar la raiz e-e sima de c
m, exact = gmpy2.iroot(c, e)

print("Resultado como entero:", m)
print("  Es raiz exacta?:", exact)

# Mostrarlo como texto (asumiendo que es ASCII/UTF-8)
mensaje = bytes.fromhex(hex(m)[2:]).decode(errors="ignore")
print("Resultado como texto:", mensaje)
```

- al poner los valores exactos del desafio y correr el programa obtengo la bandera:
```
Resultado como entero: 2756326214127165272055984685514956804577664265193753360765
¿Es raíz exacta?: True
Resultado como texto: picoCTF{t1ny_e_2fe2da79}
```
## Notas
- Ocupe la ayuda del profesor para saber que hacer para este desafio

## Referencias
