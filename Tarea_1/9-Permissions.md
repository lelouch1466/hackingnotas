## Reto
Permissions
## Descripcion
Can you read files in the root file?

Additional details will be available after launching your challenge instance.

## Solucion
- Despues de conectarse al servidor que nos dan voy al root del sistema con `cd /` y veo una carpeta llamada root
- Al tratar de abrirla para ver los contenidos me aparece un error porque mi usuario no tiene los permisos necesarios para verla
- Pense que poniendo sudo primero me dejaria hacerlo pero siguio con error
- Sin saber que hacer busco una solucion. Poniendo este comando: 
  `sudo vi -c ':!/bin/sh' /dev/null` 
  me da algo asi como una consola sin usuario donde no sirve ni tab ni flechas.
- En esta consola puedo ir hacia root con `cd ~` donde se encuentra *flag.txt* y al abrirlo con cat me da la bandera **picoCTF{uS1ng_v1m_3dit0r_55878b51}**
  
## Notas
- no tengo ni idea de que acabo de hacer

## Referencias

[PicoCTF Permissions - YouTube](https://www.youtube.com/watch?v=ZCM8pLNE2TE)
[vi | GTFOBins](https://gtfobins.github.io/gtfobins/vi/)
