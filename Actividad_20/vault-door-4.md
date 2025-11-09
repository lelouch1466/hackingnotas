
## Reto
### vault-door-4
## Descripcion
This vault uses ASCII encoding for the password.The source code for this vault is here: [VaultDoor4.java](https://challenge-files.picoctf.net/c_fickle_tempest/f587295139ec9c3d23e1299b831596c3243b0e042bec63dd21168e996c0f7c8c/VaultDoor4.java)
## Solucion
- al descargar y abrir el .java que nos dan con `nano` veo esto en la parte de abajo
```
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 067 , 065 ,
            '9' , '6' , '0' , '0' , 'a' , 'b' , 'c' , '3' ,
        };

```
- seguramente es la bandera cifrada por partes en diferentes formas
- la primera parte por las pistas que me dieron seguramente es ASCII, entonces voy a [esta pagina](https://es.rakko.tools/tools/76/) y pongo `106 85 53 116 95 52 95 98` que me devuelve `jU5t_4_b`
- despues la segunda parte parece estar en hex por tener 0x... , entonces usando cybershef pongo `0x55 0x6e 0x43 0x68 0x5f 0x30 0x66 0x5f` y me da `UnCh_0f_`
- la tercera parte no se en que estaba, pero chatgpt me dijo que era octales por los 0 que tenia a la izquierda, y usando [esta pagina](https://v2.cryptii.com/octal/text) puse `0142, 0131, 0164, 063 , 0163, 0137, 067 , 065` que me regreso `bYt3s_75`
- la ultima parte no parece tener algun cifrado asi que lo copio normal
- poniendo todo junto obtengo la bandera: **jU5t_4_bUnCh_0f_bYt3s_759600abc3**

## ALT
- como el codigo ya compara lo que demos de input con los bytes que tiene, es posible tambien lo inverso y convertir los bytes a la contrasña
- modifico un poco el codigo para que quede asi:
```
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 067 , 065 ,
            '9' , '6' , '0' , '0' , 'a' , 'b' , 'c' , '3' ,
        };

        String result = new String(myBytes);
        System.out.println("Ola k ase "+result);

        return true;
    }
```
- y ahora si corro el programa me da la bandera
```
lelouch1466-picoctf@webshell:~$ java VaultDoor4
Enter vault password: yugyukgyfkyuvyugyukgygiygygyuk
Ola k ase jU5t_4_bUnCh_0f_bYt3s_759600abc3
Access granted.
```
## Notas

## Referencias
[Texto - Ascii Converter / Translator: ascii a texto, texto a ascii | RAKKOTOOLS🔧](https://es.rakko.tools/tools/76/)

[Octal to Text - cryptii v2](https://v2.cryptii.com/octal/text)