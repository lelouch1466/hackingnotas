
## Reto
substitution0
## Descripcion
A message has come in but it seems to be all scrambled. Luckily it seems to have the key at the beginning. Can you crack this substitution cipher?Download the message [here](https://artifacts.picoctf.net/c/153/message.txt).
## Solucion
- al descargar el mensaje y abrirlo vemos esto:
```
OHNFUMWSVZLXEGCPTAJDYIRKQB 

Suauypcg Xuwaogf oacju, rvds o waoiu ogf jdoduxq ova, ogf hacywsd eu dsu huudxu
mace o wxojj noju vg rsvns vd roj ugnxcjuf. Vd roj o huoydvmyx jnoaohouyj, ogf, od
dsod dveu, yglgcrg dc godyaoxvjdj—cm ncyaju o wauod pavbu vg o jnvugdvmvn pcvgd
cm ivur. Dsuau ruau drc acygf hxonl jpcdj guoa cgu ukdauevdq cm dsu honl, ogf o
xcgw cgu guoa dsu cdsua. Dsu jnoxuj ruau uknuufvgwxq soaf ogf wxcjjq, rvds oxx dsu
oppuoaognu cm hyagvjsuf wcxf. Dsu ruvwsd cm dsu vgjund roj iuaq aueoalohxu, ogf,
dolvgw oxx dsvgwj vgdc ncgjvfuaodvcg, V ncyxf soafxq hxoeu Zypvdua mca svj cpvgvcg
aujpundvgw vd.

Dsu mxow vj: pvncNDM{5YH5717Y710G_3I0XY710G_03055505}
```
- parece ser algun tipo de encriptado pero ninguno muy aparente
- nos dice que la llave esta al principio, osea en `OHNFUMWSVZLXEGCPTAJDYIRKQB`
- si vemos esa linea podemos darnos cuenta que solo hay letras y que no hay ninguna que se repita
- hasta abajo vemos que esta la llave "{}" para la bandera lo que significa que seguramente es la bandera codificada
- si vemos bien tambien vemos que NDM seguramente signica CTF
- si vemos la llave vemos que la tercera y cuarta letra correspondem al lugar donde estaria C y F
- con esto podemos asumir que si colocamos el abecedario junto a la llave obtendremos la equivalencia de cada letra para el decifrado de esta forma
```
O H N F U M W S V Z L ...
A B C D E F G H I J K ...
```
- usando un script de python podemos hacer el decifrado automaticamente:
```
from string import ascii_uppercase, ascii_lowercase

alphabet = 'OHNFUMWSVZLXEGCPTAJDYIRKQB'

text = '''
Suauypcg Xuwaogf oacju, rvds o waoiu ogf jdoduxq ova, ogf hacywsd eu dsu huudxu
mace o wxojj noju vg rsvns vd roj ugnxcjuf. Vd roj o huoydvmyx jnoaohouyj, ogf, od
dsod dveu, yglgcrg dc godyaoxvjdj—cm ncyaju o wauod pavbu vg o jnvugdvmvn pcvgd
cm ivur. Dsuau ruau drc acygf hxonl jpcdj guoa cgu ukdauevdq cm dsu honl, ogf o
xcgw cgu guoa dsu cdsua. Dsu jnoxuj ruau uknuufvgwxq soaf ogf wxcjjq, rvds oxx dsu
oppuoaognu cm hyagvjsuf wcxf. Dsu ruvwsd cm dsu vgjund roj iuaq aueoalohxu, ogf,
dolvgw oxx dsvgwj vgdc ncgjvfuaodvcg, V ncyxf soafxq hxoeu Zypvdua mca svj cpvgvcg
aujpundvgw vd.

Dsu mxow vj: pvncNDM{5YH5717Y710G_3I0XY710G_03055505}
'''

dec = ''

for c in text:
    if c in ascii_uppercase:
        dec += ascii_uppercase[alphabet.index(c)]
    elif c in ascii_lowercase:
        dec += ascii_lowercase[alphabet.index(c.upper())]
    else:
        dec += c

print(dec)
```
- y al imprimir el mensaje obtenemos la bandera: **picoCTF{5UB5717U710N_3V0LU710N_03055505}**
```
Hereupon Legrand arose, with a grave and stately air, and brought me the beetle
from a glass case in which it was enclosed. It was a beautiful scarabaeus, and, at
that time, unknown to naturalists—of course a great prize in a scientific point
of view. There were two round black spots near one extremity of the back, and a
long one near the other. The scales were exceedingly hard and glossy, with all the
appearance of burnished gold. The weight of the insect was very remarkable, and,
taking all things into consideration, I could hardly blame Jupiter for his opinion
respecting it.

The flag is: picoCTF{5UB5717U710N_3V0LU710N_03055505}
```
## Notas

## Referencias

[Substitution0 | Cybersecurity Notes](https://ir0nstone.gitbook.io/notes/writeups/picogym/cryptography/substitution0)