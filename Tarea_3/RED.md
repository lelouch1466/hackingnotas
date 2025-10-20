
## Reto
RED
## Descripcion
RED, RED, RED, REDDownload the image: [red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)
## Solucion
- Descargamos la imagen que nos dan
- si la abrimos solo es un cuadro rojo
- si veo los metadatos no se ve nada interesante
- tal vez tenga mas cosas adentro asi que trato con `unzip` pero nada
- pienso entonces en esteganografia y que tal vez tenga mensaje oculto dentro
- como es un png uso `zsteg red.png` y me regresa un base64 *cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ*
- cuando lo pongo en cybeshef es la bandera: **picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}**
## Notas

## Referencias
