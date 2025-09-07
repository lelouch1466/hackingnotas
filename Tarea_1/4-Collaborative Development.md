## Reto
### Collaborative Development

## Descripcion
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/69/challenge.zip)

## Solucion
- despues de descargar el archivo y descomprimirlo parece solo tener un .py, pero tambien tiene una carpeta git
- trate de hacer un grep para encontrar la contraseña pero no encontre nada, busque dentro de las carpeta y tampoco encontre nada
- con las pistas vi que habia mas ramas en el proyecto y vi que habia ramas con partes 1,2 y3
- con esto pense que lo que tenia que hacer es combinar las ramas dentro de main para encontrar la bandera, pero no sabia como hacerlo, trate de aplicar un pull pero no funcionaba
- Despues de revisar una soluvion vi que para cambiar de rama se usa `git checkout [nombre rama]` y con este comando fui cambiando de ramas
- En cada rama abri el .py que tenian y cada una tenia una parte de la bandera:
  
print("picoCTF{t3@mw0rk_", end='')
print("m@k3s_th3_dr3@m_", end='')
print("w0rk_e4b79efb}")

- poniendo todo juntome queda : **picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_e4b79efb}**

## Notas
- Otra solucion que vi es juntar todas las ramas como habia pensado, pero era mucho mas larga y complicada por los conflictos de mergeo

## Referencias
[Collaborative Development Pico CTF 2024 Walkthrough | General Skills](https://www.youtube.com/watch?v=_CH5IQewkzw)
[PicoCTF Collaborative Development](https://www.youtube.com/watch?v=RLGp4GWd-k4)