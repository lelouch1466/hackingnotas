
## Reto
### Pixelated
## Descripcion
I have these 2 images, can you make a flag out of them? [scrambled1.png](https://mercury.picoctf.net/static/e8054e22552c6aba591cdf7440eb25e4/scrambled1.png) [scrambled2.png](https://mercury.picoctf.net/static/e8054e22552c6aba591cdf7440eb25e4/scrambled2.png)
## Solucion
- nos dan 2 imagenes pero no podemos ver nada en ellas
- si vemos sus metadatos o buscamos con zsteg no vemos nada
- por la pista nos dan una forma de cryptografia en donde superponemos ambas imagenes juntas
- para hacer esto le pedi al chatgot hacer este script:
```
from PIL import Image  
  
def combine_images(image1_path, image2_path, output_path):  
# Open the images  
image1 = Image.open(image1_path)  
image2 = Image.open(image2_path)  
  
# Ensure both images have the same size  
if image1.size != image2.size:  
raise ValueError("Images must have the same size")  
  
# Combine the images using a simple averaging technique  
combined_image = Image.blend(image1, image2, alpha=0.5)  
  
# Save the combined image  
combined_image.save(output_path)  
  
if __name__ == "__main__":  
# Provide the paths of the input images and the desired output path  
image1_path = "scrambled1.png"  
image2_path = "scrambled2.png"  
output_path = "combined_image.png"  
  
combine_images(image1_path, image2_path, output_path)
```
- ahora tenemos la imagen convinada pero solo vemos todo gris
![](../Imagenes/combined_image.png)
- pero si le hacemos un zoom grande podemos ver un punto azul y algo muy pero muy tenue alrededor del punto
- llendo a [esta pagina](https://29a.ch/photo-forensics/#forensic-magnifier) podemos subir nuestra imagen y cambiar las opciones para que la imagen se vea diferente, despues de jugar un poco con las opciones encuentro la bandera por donde esta el punto : **picoCTF{d72ea4af}**
![](../Imagenes/Pasted%20image%2020251029154942.png)
## Notas

## Referencias
[Visual cryptography - Wikipedia](https://en.wikipedia.org/wiki/Visual_cryptography)
[Pixelated picoCTF2021 | Write-up. Hello guys, this is one of my favorite… | by Alireza Ghorbani | Medium](https://medium.com/@alireza.ghorbani/pixelated-picoctf-write-up-0b767d322256)
[Forensically, free online photo forensics tools - 29a.ch](https://29a.ch/photo-forensics/#forensic-magnifier)