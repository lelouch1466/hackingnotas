
## Reto
### substitution1
## Descripcion
A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again.Download the message [here](https://artifacts.picoctf.net/c/183/message.txt).
## Solucion
- Nos dan el siguiente mensaje:
```
LKOb (bwvek ove lgqkhej kwj osgx) gej g kyqj vo lvrqhkje bjlhetky lvrqjktktvu. Lvukjbkgukb gej qejbjukjz dtkw g bjk vo lwgssjuxjb dwtlw kjbk kwjte lejgktftky, kjlwutlgs (guz xvvxstux) bitssb, guz qevmsjr-bvsftux gmtstky. Lwgssjuxjb hbhgssy lvfje g uhrmje vo lgkjxvetjb, guz dwju bvsfjz, jglw ytjszb g bketux (lgssjz g osgx) dwtlw tb bhmrtkkjz kv gu vustuj blvetux bjeftlj. LKOb gej g xejgk dgy kv sjgeu g dtzj geegy vo lvrqhkje bjlhetky bitssb tu g bgoj, sjxgs juftevurjuk, guz gej wvbkjz guz qsgyjz my rguy bjlhetky xevhqb gevhuz kwj dvesz ove ohu guz qeglktlj. Ove kwtb qevmsjr, kwj osgx tb: qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}
```

- y por las pistas sabemos que seguramente sera una sustitucion de la misma manera que en [substitution0](substitution0.md) pero esta vez no tenemos la llave
- pero sabemos que el mensaje SÍ dice algo y que al final, `qtlvLKO{OE3AH3ULY_4774LI5_4E3_L001_6J0659OM}` es la bandera
- podemos empezar a hacer nuestra propia llave ya que inferimos que `qtlvLKO = picoCTF` 
- viendo el mensaje veo que hay muchas veces donde 'g' aparece sola, y la unica letra que pienso que puede hacer eso es 'a'
- tomando como base el codigo de [substitution0](substitution0.md), le pedi al chat que me hiciera este codigo, donde le doy lo que llevo resuelto de la llave e imprima el mensaje con letras cifradas, y las que no, imprime '?'

```
from string import ascii_uppercase

cipher_key = "[cifrado aqui]"

# Crear diccionario solo con letras conocidas
decrypt_map = {cipher: plain for plain, cipher in zip(ascii_uppercase, cipher_key) if cipher.isalpha()}

text = " [mensaje aqui] "

dec = ""

for c in text:
    if c.upper() in decrypt_map:
        # Letra conocida → descifrar
        out = decrypt_map[c.upper()]
        dec += out if c.isupper() else out.lower()
    elif c.upper() in ascii_uppercase:
        # Letra que corresponde a '?' → imprimir '?'
        dec += '?' if c.isupper() else '?'
    else:
        # Todo lo demás (símbolos, números, espacios) se deja igual
        dec += c

print(dec)
```

- con el codigo listo mi primera version del cifrado es este: `v1. G?L??O??T?????VQ???K??????` (cada posicion es la letra que corresponde en el abecedario. ej: G=A ,L=C) y el resultado del mensaje fue:

```
V1
---
CTF? (??o?t fo? capt??? t?? f?a?) a?? a t?p? of co?p?t?? ??c??it? co?p?titio?. Co?t??ta?t? a?? p?????t?? ?it? a ??t of c?a??????? ??ic? t??t t??i? c??ati?it?, t?c??ica? (a?? ?oo??i??) ??i???, a?? p?o????-?o??i?? a?i?it?. C?a??????? ???a??? co??? a ?????? of cat??o?i??, a?? ???? ?o????, ?ac? ?i???? a ?t?i?? (ca???? a f?a?) ??ic? i? ????itt?? to a? o??i?? ?co?i?? ????ic?. CTF? a?? a ???at ?a? to ??a?? a ?i?? a??a? of co?p?t?? ??c??it? ??i??? i? a ?af?, ???a? ???i?o????t, a?? a?? ?o?t?? a?? p?a??? ?? ?a?? ??c??it? ??o?p? a?o??? t?? ?o??? fo? f?? a?? p?actic?. Fo? t?i? p?o????, t?? f?a? i?: picoCTF{F?3??3?C?_4774C?5_4?3_C001_6?0659F?}
```

- sin letras que me distraigan puedo empezar a inferir que dicen algunas palabras, por ejemplo al principio "**fo? capt??? t?? f?a?**" dedusco que esta diciendo "**for capture the flag**"
- siguiendo esta logica reviso el resto del mensaje y me quedo con mi segunda vercion del cifrado: `v2. G?L?JOXWT?CS??VQ?E?KH???Y?`, y lo vuelvo a poner en mi script para obtener un mensaje mas claro:

```
V2
---
CTF? (?hort for capture the flag) are a type of co?puter ?ecurity co?petitio?. Co?te?ta?t? are pre?e?te? ?ith a ?et of challe?ge? ?hich te?t their creati?ity, tech?ical (a?? googli?g) ??ill?, a?? pro?le?-?ol?i?g a?ility. Challe?ge? u?ually co?er a ?u??er of categorie?, a?? ?he? ?ol?e?, each yiel?? a ?tri?g (calle? a flag) ?hich i? ?u??itte? to a? o?li?e ?cori?g ?er?ice. CTF? are a great ?ay to lear? a ?i?e array of co?puter ?ecurity ??ill? i? a ?afe, legal e??iro??e?t, a?? are ho?te? a?? playe? ?y ?a?y ?ecurity group? arou?? the ?orl? for fu? a?? practice. For thi? pro?le?, the flag i?: picoCTF{FR3?U3?CY_4774C?5_4R3_C001_6E0659F?}
```

- ahora basicamente ya puedo leer todo el mensaje excpeto por algunas palabras
- sigo el mismo procedimiento anterior para conseguir mi tercera y ultima vercion del cifrado: `v3. GMLZJOXWT?CSRUVQ?EBKH?D?Y?`
- y ahora el mensaje me queda asi:
```
V3
---
CTFs (short for capture the flag) are a type of computer security competition. Contestants are presented with a set of challenges which test their creati?ity, technical (and googling) s?ills, and problem-sol?ing ability. Challenges usually co?er a number of categories, and when sol?ed, each yields a string (called a flag) which is submitted to an online scoring ser?ice. CTFs are a great way to learn a wide array of computer security s?ills in a safe, legal en?ironment, and are hosted and played by many security groups around the world for fun and practice. For this problem, the flag is: picoCTF{FR3?U3NCY_4774C?5_4R3_C001_6E0659FB}
```
- aunque aun me quedan letras por decifrar, el mensaje y la badera ya son legibles
- solo me faltan 2 letras para la bandera pero es facil deducir cuales son para obtenerla completa: **picoCTF{FR3QU3NCY_4774CK5_4R3_C001_6E0659FB}**

## Notas
- La unica razon por la que batalle fue para que el chatgpt me diera un codigo que si imprimiera ? en vez de letras :v
- fue despues de haberlo resuelto, pero tambien pude haber usado el resolvedor online de substitucion para este problema tambien

## Referencias
