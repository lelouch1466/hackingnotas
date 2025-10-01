
## Reto
Rust fixme 1

## Descripcion
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).

## Solucion
- al descargar el archivo es un fixme1.tar.gz
- para descomprimirlo pongo `tar -xvzf fixme1.tar.gz`
- me crea un directorio llamado fixme1
- para correlo entro al directorio y trato de compilarlo con `cargo build`
- al intentantarlo me marco unos errores en la terminal
- busco el src del rust y lo abro con mousepad
- dentro veo que lo que hay que arreglar esta en comentarios tambien
	1. Hay una linea que no se cerro con ';'
	2. Hay un return que solo se puso como ret
	3. el println le falta {}

- arreglo esto y trato de compilarlo de nuevo
- esta vez funciona y solo lo corro con `cargo run` y me regresa la bandera **picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}**

## Notas
- no se nada de rust pero los problemas de compilacion me decian exactamente que faltaba pero tambien segui una guia para ver que estaba mal con println

## Referencias
[How to solve Rust Fixme 1](https://www.youtube.com/watch?v=g1AbiC8DdYw)
