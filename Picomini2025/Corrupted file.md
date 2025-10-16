
## Reto
Corrupted file

## Descripcion
This file seems broken... or is it? Maybe a couple of bytes could make all the difference. Can you figure out how to bring it back to life?Download the file [here](https://challenge-files.picoctf.net/c_amiable_citadel/913cc89502ac17f0c3cb28c10eff77ca19d19b5e5bce22ff24775a6825b6f2d3/file).

## Solucion
Pistas: checar header, jpeg, usar xxd
### FALLOS
- al descargar el archivo veo que solo dice 'file' sin ninguna extencion
- trate de abrirlo con notepad pero nada
- trate de darle .txt de extencion para ver si cambiaba algo pero nada
- al ver las pistas pense que al darle la extencion .jpeg y abrilo esto funcionaria pero no
- trate de ver los metadatos pero nada
- usando strings o cat y buscando con grep pero nada
- con la ultima pista trate de decodificar con xxd y buscando con grep pero nada

### FORMA CORRECTA
- Cuando ya ni sabia que hacer mejor le pregunte al chatgpt
- primero aplicamos un `file file` para ver que tipo es y solo regresa que es data
- checamos los primero bits con `xxd -l 64 file | less` y nos aparece esto
```
00000000: 5c78 ffe0 0010 4a46 4946 0001 0100 0001 \x....JFIF...... 00000010: 0001 0000 ffdb 0043 0008 0606 0706 0508 .......C........ 00000020: 0707 0709 0908 0a0c 140d 0c0b 0b0c 1912 ................ 00000030: 130f 141d 1a1f 1e1d 1a1c 1c20 242e 2720 ........... $.
```
- por la pista y como vemos que tiene JFIF sabemos que debe ser un JPEG, y los primeros bits de un JPEG deben ser **FF D8**
- como vemos en la primera linea hay '\x' que es basura y debemos quitarlo, lo hice haciendo esto: `dd if=file of=extracted.jpg bs=1 skip=2` y se creo una nueva imagen llamada extracted.jpg
- si vuelvo a checar extracted.jpg con `file` veo que sigue siendo data, vuelvo a checar los primeros bites y ahora veo esto:
```
00000000: ffe0 0010 4a46 4946 0001 0100 0001 0001 ....JFIF........ 00000010: 0000 ffdb 0043 0008 0606 0706 0508 0707 .....C.......... 00000020: 0709 0908 0a0c 140d 0c0b 0b0c 1912 130f ................ 00000030: 141d 1a1f 1e1d 1a1c 1c20 242e 2720 222c ......... $.' ",
```
- ya empieza con ff pero aun no tiene d8
- hago el siguiente comando para modificarlo: `printf '\xFF\xD8' | cat - extracted.jpg > fixed.jpg`
- se crea la imagen fixed.jpg y ahora si la checo con `file` ya me dice que es un JPEG
- Al abrir la imagen me aparece una imagen de baja calidad con la bandera: **picoCTF{r3st0r1ng_th3_by73s_752d2c00}**
## Notas
- aqui pondre exactamente que hicieron los 2 comandos para recuperar la imagen

## 1️⃣ `dd if=file of=extracted.jpg bs=1 skip=2`

- **`dd`**: copia datos byte a byte.
    
- **`if=file`**: _input file_ → tu archivo original sin extensión.
    
- **`of=extracted.jpg`**: _output file_ → el archivo reparado provisional.
    
- **`bs=1`**: _block size_ de 1 byte (lee/escribe de a 1 byte).
    
- **`skip=2`**: salta los primeros 2 bloques (como bs=1, son **2 bytes**).
    

👉 En tu caso, servía para **quitar los 2 bytes basura `5C 78`** que estaban antes de los datos válidos del JPEG.  
Así el nuevo archivo `extracted.jpg` empezó directamente en lo que seguía (pero todavía le faltaba la cabecera correcta `FFD8`).

---

## 2️⃣ `printf '\xFF\xD8' | cat - extracted.jpg > fixed.jpg`

Este comando construye un archivo nuevo pegando **la cabecera correcta** al inicio:

- **`printf '\xFF\xD8'`** → genera exactamente 2 bytes (`FF D8`), que son la firma mágica (_Start of Image_) de un JPEG válido.
    
- **`cat - extracted.jpg`** → `cat` concatena dos entradas:
    
    - `-` significa _leer de stdin_ (los bytes que vinieron del `printf`).
        
    - `extracted.jpg` es tu archivo reparado parcialmente.
        
- **`>`** → redirige todo a `fixed.jpg`.
    

👉 Resultado: `fixed.jpg` empieza con `FF D8` seguido de los datos de `extracted.jpg`.  
Ahora sí, `fixed.jpg` tiene un **header válido de JPEG** y puede ser reconocido por `file`, `xdg-open`, etc.

---

## 🔎 En resumen

- El primer comando (`dd ... skip=2`) → **quita bytes basura**.
    
- El segundo (`printf ... | cat ...`) → **reconstruye el header correcto** agregando los bytes faltantes.
    

Eso hizo que tu archivo “misterioso” finalmente fuera reconocido como **JPEG válido**.


## Referencias
