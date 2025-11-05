
## Reto
### hashcrack
## Descripcion
A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?Access the server using `nc verbal-sleep.picoctf.net 50350`
## Solucion
- al conectarnos al netcat nos dan un cifrado y nos pregunta por la contraseña que deciframos
- usando [esta pagina)](https://md5hashing.net/hash) puedo poner el cifrado que nos den y buscar por todos los tipos de hash para encontrarle solucion...aunque a veces si tarda bastante
- despues de 3 contraseñas resueltas nos da la bandera:**picoCTF{UseStr0nG_h@shEs_&PaSswDs!_4de57566}**
- 
![](../Imagenes/Pasted%20image%2020251103160128.png)

![](../Imagenes/Pasted%20image%2020251103155306.png)
![](../Imagenes/Pasted%20image%2020251103155654.png)

![](../Imagenes/Pasted%20image%2020251103155817.png)

## Notas

## Referencias
[Hash decoder and calculator (hash and unhash)](https://md5hashing.net/hash)