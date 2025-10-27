
## Reto
### miniRSA
## Descripcion
Let's decrypt this: [ciphertext](https://jupiter.challenges.picoctf.org/static/eb5e6df8e14c52873cf88c582a1a4008/ciphertext)? Something seems a bit small.
## Solucion
- nos dan estos valores en el archivo:
```

N: 29331922499794985782735976045591164936683059380558950386560160105740343201513369939006307531165922708949619162698623675349030430859547825708994708321803705309459438099340427770580064400911431856656901982789948285309956111848686906152664473350940486507451771223435835260168971210087470894448460745593956840586530527915802541450092946574694809584880896601317519794442862977471129319781313161842056501715040555964011899589002863730868679527184420789010551475067862907739054966183120621407246398518098981106431219207697870293412176440482900183550467375190239898455201170831410460483829448603477361305838743852756938687673
e: 3

ciphertext (c): 2205316413931134031074603746928247799030155221252519872650080519263755075355825243327515211479747536697517688468095325517209911688684309894900992899707504087647575997847717180766377832435022794675332132906451858990782325436498952049751141 
```

- los pongo en la calculadora rsa y me da la bandera :v 
- **picoCTF{n33d_a_lArg3r_e_d0cd6eae}**

## Notas
- el punto de este ejercicio es no usar un valor de e pequeño porque podemos "despejar" la formula de m para que no quede: `m ≡ c^d (mod n)​` (explicacion de esto mas abajo) y como e es muy pequeño podemos calcular facimente esto, a diferencia de que si e fuera grande no podriamos calcularlo

## Explicacion de m = c^d  (mod n)
Tienes la congruencia:

c≡me(modn).c \equiv m^e \pmod{n}.c≡me(modn).

Tu objetivo es **despejar mmm**.

En los números reales, despejar una potencia es “elevar ambos lados a la inversa del exponente”, o sea:

m=c1/e.m = c^{1/e}.m=c1/e.

Pero en **aritmética modular** no existen raíces ni divisiones directas: no hay “dividir por eee” así sin más.  
👉 Lo que sí existe es el **inverso modular**.

---

## 🔹 Paso 1: Recordar qué significa “inverso modular”

Decimos que un número ddd es el **inverso modular de eee módulo φ(n)\varphi(n)φ(n)** si:

e⋅d≡1(modφ(n)).e \cdot d \equiv 1 \pmod{\varphi(n)}.e⋅d≡1(modφ(n)).

Eso quiere decir que:

e⋅d=1+kφ(n)e \cdot d = 1 + k \varphi(n)e⋅d=1+kφ(n)

para algún número entero kkk.

Esta relación será la clave para “anular” el exponente eee.

---

## 🔹 Paso 2: Elevamos ambos lados a la potencia ddd

Partimos de:

c≡me(modn).c \equiv m^e \pmod{n}.c≡me(modn).

Elevamos **ambos lados** a la potencia ddd:

cd≡(me)d(modn).c^d \equiv (m^e)^d \pmod{n}.cd≡(me)d(modn).

Por las reglas de los exponentes:

(me)d=me⋅d.(m^e)^d = m^{e \cdot d}.(me)d=me⋅d.

Sustituyamos lo que sabemos de arriba:

e⋅d=1+kφ(n).e \cdot d = 1 + k\varphi(n).e⋅d=1+kφ(n).

Entonces:

me⋅d=m1+kφ(n)=m⋅(mφ(n))k.m^{e \cdot d} = m^{1 + k\varphi(n)} = m \cdot (m^{\varphi(n)})^k.me⋅d=m1+kφ(n)=m⋅(mφ(n))k.

---

## 🔹 Paso 3: Aplicamos el teorema de Euler

El **teorema de Euler** dice:

mφ(n)≡1(modn),si gcd⁡(m,n)=1.m^{\varphi(n)} \equiv 1 \pmod{n}, \quad \text{si } \gcd(m,n) = 1.mφ(n)≡1(modn),si gcd(m,n)=1.

Entonces:

(mφ(n))k≡1k≡1(modn).(m^{\varphi(n)})^k \equiv 1^k \equiv 1 \pmod{n}.(mφ(n))k≡1k≡1(modn).

Por tanto:

me⋅d≡m⋅1≡m(modn).m^{e \cdot d} \equiv m \cdot 1 \equiv m \pmod{n}.me⋅d≡m⋅1≡m(modn).

---

## 🔹 Paso 4: Sustituimos en la ecuación

Regresamos a:

cd≡(me)d≡me⋅d≡m(modn).c^d \equiv (m^e)^d \equiv m^{e \cdot d} \equiv m \pmod{n}.cd≡(me)d≡me⋅d≡m(modn).

Y ahí está el despeje:

m≡cd(modn),\boxed{m \equiv c^d \pmod{n}},m≡cd(modn)​,

donde ddd es el número que satisface:

e⋅d≡1(modφ(n)).\boxed{e \cdot d \equiv 1 \pmod{\varphi(n)}}.e⋅d≡1(modφ(n))​.

---

## 🔹 Paso 5: Interpretación intuitiva

👉 En resumen:

- La operación “elevar a eee” tiene como “inversa” modular la operación “elevar a ddd”.
    
- Pero esa inversión solo es válida **módulo φ(n)\varphi(n)φ(n)** (no módulo nnn directamente).
    
- La relación e⋅d≡1(modφ(n))e \cdot d \equiv 1 \pmod{\varphi(n)}e⋅d≡1(modφ(n)) es **la forma modular de decir “multiplicar por 1/e”**.
    

Por eso, en RSA, eee se usa para **cifrar** y ddd para **descifrar**.

---

## 🔹 Ejemplo corto

Supón:

- n=33=3×11⇒φ(n)=20.n = 33 = 3 \times 11 \Rightarrow \varphi(n) = 20.n=33=3×11⇒φ(n)=20.
    
- e=7.e = 7.e=7.
    

Buscamos ddd tal que 7d≡1(mod20)7d \equiv 1 \pmod{20}7d≡1(mod20).

7×3=21≡1(mod20)7 \times 3 = 21 \equiv 1 \pmod{20}7×3=21≡1(mod20).  
✅ Entonces d=3.d = 3.d=3.

Y el despeje queda:

m≡c3(mod33).m \equiv c^3 \pmod{33}.m≡c3(mod33).

## Referencias
[RSA Cipher Calculator - Online Decoder, Encoder, Translator](https://www.dcode.fr/rsa-cipher)