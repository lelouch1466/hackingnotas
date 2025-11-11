
## Reto
### Picker II
## Descripcion
Can you figure out how this program works to get the flag?Connect to the program with netcat:`$ nc saturn.picoctf.net 60371`The program's source code can be downloaded [here](https://artifacts.picoctf.net/c/521/picker-II.py).
## Solucion
- igual que en picker 1, cuando nos conectamos parece que nos pregunta por una funcion para correr
- al revisar el codigo fuente veo que no puedo simplemente poner "win" ya que tiene un "filtro" que previene especificamente escribir eso
- lo que se me viene a la mente entonces es usar algo como las wildcards, alguna forma de escribir algo totalmente diferente pero que el programa interprete como win
- despues de preguntarle al char como hacerlo me dio esto:
```
globals()['w'+'i'+'n']
```
- que el programa va a interpretar como win, y al ponerlo me dio un hexa que cuando lo pongo en el cybershef es la bandera:**picoCTF{f1l73r5_f41l_c0d3_r3f4c70r_m1gh7_5ucc33d_b924e8e5}**
## Notas

## Referencias
(char)119+(char)105+(char)110