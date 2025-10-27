
## Reto
### b00tl3gRSA3
## Descripcion
Why use p and q when I can use more? Connect with `nc jupiter.challenges.picoctf.org 3726`.
## Solucion
- al conectarnos nos dan estos valores:
```
c: 97751811532942234454261688047414958388252063186247854093854626852253903184796228359403289239741501215088638968453239587967788174879400285558918963382615899474444983860742989965685716286709815470502976984126909411743848638806543171810637714247823968692440673970823122127402664014183161597856353183501375015460811541213105293857613139797290491988
n: 172651894422604977059610329410594073414329587459048648241710698666723243394259546407354892021095428859733422596509328124789964129237483932376392841806549938250357293149615250604607140903940874548860291380922952912320905717509999835780083718508902940239696677075085432772509631419715362992086671786171203776663765762252017008024346696882603610047
e: 65537
```
- pero ahora si lo intentamos poner en la calculadora solo nos da simbolos sin sentido
- mas abajo en la pagina podemos que tiene la opcion de encontrar factores
- si le damos el valor de n para buscar sus factores vemos que no son 2 factores ("p" y "q") que conforman el numero, si no varios
- nuestra formula para calcular `d = e^-1 (mod tn)` necesitamos tn que en su formula `tn = (p-1)*(q-1)` solo tiene 2 factores, pero no necesariamente esta completa, queda mas bien asi: 
x_1 = $x_1$ 
x = un factor
```
tn = (x_1 - 1) * (x_2 - 1) * (x_3 - 1) * ... (x_n - 1) 
```
- entonces para sacar "tn" solo tenemos que restarle 1 a cada factor y multiplicarlos todos
- podemos hacer esto con algun script pero yo use [Integer factorization calculator](https://www.alpertron.com.ar/ECM.HTM), cuado le di n me regreso "euler's totient" o tn que es lo que busco,
- ahora regrese a la calculadora rsa y puse mi tn donde dice: "Intermediate value Phi (Integer) φ=" y ahora si me regreso la bandera: **picoCTF{too_many_fact0rs_8606199}**
## Notas
- si tuve que revisar bastantes writeups para entender que se estaba haciendo

## Referencias
[Prime Factors Decomposition - Online Factorization Calculator](https://www.dcode.fr/prime-factors-decomposition)

[PicoCTF b00tl3gRSA3](https://www.youtube.com/watch?v=-EXKqVfYmCU)

[RSA Cipher Calculator - Online Decoder, Encoder, Translator](https://www.dcode.fr/rsa-cipher)

[Integer factorization calculator](https://www.alpertron.com.ar/ECM.HTM)

[picoCTF 2019 b00tl3gRSA3 Write-Up](https://plasticuproject.com/posts/b00tl3grsa3-write-up/)