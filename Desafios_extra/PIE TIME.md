
## Reto
### PIE TIME
## Descripcion
Can you try to get the flag? Beware we have PIE!

Additional details will be available after launching your challenge instance.
## Solucion
- me dan un netcat para conectarme
- al conectarme me dicen el adress de main, algo asi como: `0x60bca649b33d`
- pero cada vez que me conecto cambia el adress
- esto es porque corre con PIE (Position-Independent Executable file), y lo podemos verificar usando este comando sobre el binario `readelf -h vuln | grep "Type:"`
- nos pide que pongamos el adress de alguna funcion para que se ejecute
- de las cosas que nos dan son el codigo fuente y el binario del programa
- viendo el programa vemos que si queremos obtener la bandera debemos correr la funcion `win()`
- como tenemos el binario corremos 
```
readelf -s vuln | egrep '\b(main|win)\b'
```
- y esto nos da el offset entre el metodo main() y win()
```
    66: 00000000000012a7   150 FUNC    GLOBAL DEFAULT   16 win
    70: 000000000000133d   204 FUNC    GLOBAL DEFAULT   16 main
```
- volvemos a entrar al netcat y apuntamos el adress de main que nos da para correr este script en otra terminal:
```
#!/bin/bash
# Ajusta LEAK_MAIN si tienes otro leak; si no, deja el valor que ya conoces.
LEAK_MAIN= $valor_adress_main$


# Extraer offsets desde el binario (readelf suele mostrar el valor sin 0x)
# O pon directamente los valores que encontraste
# - `sym_win = 0x12a7`    
# - `sym_main = 0x133d`
SYM_MAIN=0x$(readelf -s vuln | awk '/ main$/ {print $2; exit}')
SYM_WIN=0x$(readelf -s vuln | awk '/ win$/ {print $2; exit}')


echo "sym_main = $SYM_MAIN"
echo "sym_win  = $SYM_WIN"
echo "leak_main = $LEAK_MAIN"

# calcular base y win address
BASE=$((LEAK_MAIN - SYM_MAIN))
WIN_ADDR=$((BASE + SYM_WIN))

printf "calculated base = 0x%x\n" $BASE
printf "calculated win  = 0x%x\n" $WIN_ADDR
```
- esto me da el adress de win, al ponerlo me da la bandera: **picoCTF{b4s1c_p051t10n_1nd3p3nd3nc3_28a46dcd}**
## Notas
- aunque me dieron el script, mejor le dije a chatgot que me hiciera el calculo
## Referencias
