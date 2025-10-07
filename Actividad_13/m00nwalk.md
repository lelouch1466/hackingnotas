
## Reto
m00nwalk

## Descripcion
Decode this [message](https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav) from the moon.

## Solucion
- reviso que tipo de archivo y es un archivo de audio
- al abrirlo se oyen sonido extraños en cierta frecuencia, parece ser algun mensaje
- descargo un decodificador de SSTV con los siguientes comandos
```
cd /opt 
sudo git clone https://github.com/colaclanth/sstv 
cd sstv
(aqui hay un readme de como instalarlo)
sudo python setup.py install
```
- una vez instalado corro el siguiente comando para decifrarlo:
```
stv -d ~/pico/message.wav -o ~/pico/flagmessage.png
```
- esto me crea una imagen y al abrila encuentro la bandera:**pico{beep_boop_im_in_space}**

## Notas

## Referencias
