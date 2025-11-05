
## Reto
### Flag in Flame
## Descripcion
The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log.Download the encoded data here: [Logs Data](https://challenge-files.picoctf.net/c_amiable_citadel/34c1721086e2555cb8df9a09fcad35cfc09a2844bbc990dd022efca838b4e6ea/logs.txt). Be prepared—the file is large, and examining it thoroughly is crucial .
## Solucion
- al descargar el archivo veo si lo trato de abrir se tarda bastante porque si esta muy largo
- por la pista que me dan y por lo que se alcanza a ver al abrirlo, seguramento es codigo en base64
- para decifrarlo le pregunto al chatgpt como hacerlo y veo que puedo hacerlo haciendo esto:
```
base64 -d logs.txt > decoded.bin
```
- con el -d lo decodifica y me deja la salida en `decoded.bin`
- siendo bin cualquier tipo de archivo pero sin especificar
- le hago un `file decoded.bin` y me dice que es un PNG
- le cambio la extencion con `mv decoded.bin decoded.png` y lo abro para ver una imagen:
![](../Imagenes/decoded.png)
- veo que abajo en la imagen hay numeros y letras, entonces los copio para obtener esto:
```
7069636F4354467B666F72656E736963735F616E616C797369735F69735F616D617A696E675F61633165333538347D
```

- lo pongo en cybershef y me dice que es Hex el cual es la bandera:
  **picoCTF{forensics_analysis_is_amazing_ac1e3584}**
## Notas

## Referencias
