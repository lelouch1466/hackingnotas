
## Reto
Input Injection 1

## Descripcion
A friendly program wants to greet you… but its goodbye might say more than it should. Can you convince it to reveal the flag?

Additional details will be available after launching your challenge instance.

## Solucion
- nos dan el codigo fuente del programa que se corre al entrar a la conexion que nos dan
- primero entro al sistema, lo unico que hace es preguntar por nuestro nombre y despues nos dice goodbye
- pero despues de eso se imprime la palabra Linux
- revisemos el codigo fuente:
```
#include <string.h>
#include <stdio.h>
#include <stdlib.h> 

void fun(char *name, char *cmd);

int main() {
    char name[200];
    printf("What is your name?\n");
    fflush(stdout);


    fgets(name, sizeof(name), stdin);
    name[strcspn(name, "\n")] = 0;

    fun(name, "uname");
    return 0;
}

void fun(char *name, char *cmd) {
    char c[10];
    char buffer[10];

    strcpy(c, cmd);
    strcpy(buffer, name);

    printf("Goodbye, %s!\n", buffer);
    fflush(stdout);
    system(c);
}


```
- observamos 3 cosas importantes:
	1. al principio guarda el nombre como un char de 200 caracteres
	2. la funcion fun() resive nuestro nombre y un comando cmd
	3. dentro de la funcion fun se copian los valores de los argumentos mandados en nuevas varibles con strcpy
- podemos ver que la razon por la que escribe linux al final es porque esta realizando `system(c)`, c lo esta copiando del argumento cmd que contiene **uname** por lo que esta realizando `system("uname")` que regresa el sistema operativo
- mas importante, esta pasando name, un char[200] a un char[10] por lo que puede ocacionar un overflow
- un overflow manda los caracteres que sobran a la siguiente variable disponible cambiando totalmente la variable incluso si ya tiene valor definido en el codigo
- sabiendo esto pondre un nombre de 10 caracteres y despues pondre un comando que sobreescriba "uname"
![[Pasted image 20251002233745.png]]
- podemos ver que dejo de decir linux e imprimio mi echo
- ahora solo hago un ls que me muestra la flag.txt y lo abro con un cat para obtener la bandera: **picoCTF{0v3rfl0w_c0mm4nd_22530a1b}**
![[Pasted image 20251002235926.png]]


## Notas

- chatgpt si me ayudo mucho a entender que estaba pasando pero nunca me dio una respuesta directa
## Referencias
![[Pasted image 20251002233745.png]]