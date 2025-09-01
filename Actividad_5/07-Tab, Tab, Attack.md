
## Reto
Tab, Tab, Attack

## Descripcion
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/a350754a299cb58988d6d47aed5be3ba/Addadshashanammu.zip)

## Solucion
- Despues de descargar y descomprimir el archivo me da un directorio con muchas carpetas dentro de carpetas
- Solo use cd y preciona muchas veces tab hasta llegar al final donde esta el archivo fang-of-haynekhtnamet 
- Primero trato de usar cat sobre el archivo pero no me da nada legible
- Despues uso strings para abrirlo y encuentro la bandera **picoCTF{l3v3l_up!_t4k3_4_r35t!_a00cae70}**

## Notas
- No hubo mucho problema con este desafio, parece mas una practica para ser mas habil en la terminal
- Al final del desafio hago un cd ~ para regresar al root
## Referencias
