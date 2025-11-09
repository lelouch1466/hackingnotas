
## Reto
### vault-door-3
## Descripcion
This vault uses for-loops and byte arrays.The source code for this vault is here: [VaultDoor3.java](https://challenge-files.picoctf.net/c_fickle_tempest/efe249b50ae104ab4d1c33f14838fda6b584138e36739834ac7cb4cb29f5b2d2/VaultDoor3.java)
## Solucion
- al descargar el archivo .java que nos dan y abrirlo con `nano` vemos que tiene una funcion para checcar contraseña
- aunque si viene algo que parece ser la bandera `jU5t_a_sna_3lpm15g64e_u_4_m1r74d`, si tratamos de ponerla no nos da nada
- al analizar un poco la funcion veo que lo que hacer es tomar partes de la contraseña que nosotros le ponemos, y armar un nuevo string que debe ser igual a lo que pensamos es la bandera
- primero toma los primeros 8 caracteres, despues los caracteres del 15 al 7, y asi se va formando la contraseña
- para no tener que estar contando y calculando que caracter poner, modifique el codigo de esta forma:
```
    public boolean checkPassword(String pas) {

        char[] buffer = new char[32];
        int i;
        String password = "jU5t_a_sna_3lpm15g64e_u_4_m1r74d";

        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        System.out.println("ola k ase "+s);
        return s.equals("jU5t_a_sna_3lpm15g64e_u_4_m1r74d");
    }
```
- le quite que cheque por la longitud de la contraseña
- cambie el nombre del argumento que le pasaba (nuestro input) para que no lo tomara en cuenta en nada
- le puse `String password = "jU5t_a_sna_3lpm15g64e_u_4_m1r74d";` para que tomaraese encuenta
- y al final imprimo lo que halla en el buffer
- al correr el programa ahora ya me dio la bandera: **picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_e1675d}**
```
lelouch1466-picoctf@webshell:~$ java VaultDoor3
Enter vault password: euicanbwuid
ola k ase jU5t_a_s1mpl3_an4gr4m_4_u_e1675d
Access denied!
```
## Notas

## Referencias

