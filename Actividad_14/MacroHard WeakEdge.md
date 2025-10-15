
## Reto
MacroHard WeakEdge

## Descripcion
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/3944a59474f9f676942282c50b9c3675/Forensics%20is%20fun.pptm)

## Solucion
- al descargarlo es un archivo .pptm
- si le hacemos un file dice que solo es una presentacion de powerpoint
- cuando le hacemos exiftool nos sale demasiada informacion que hasta se repite
- esto nos indica que al igual que en matryoshka doll, seguramente tiene archivos ocultos
- le hacemos un unzip y nos genera varias cosas e interesantemente hay esta linea:
```
inflating: ppt/slideMasters/hidden  
```
- como llama la atencion vamos hasta ese archivo y es solo una cadena ASCII
- cuando la ponemos en el cybershef para base64 nos regresa la bandera: **picoCTF{D1d_u_kn0w_ppts_r_z1p5}**
 
## Notas

## Referencias
