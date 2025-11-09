
## Reto
### vault-door-5
## Descripcion
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding!The source code for this vault is here: [VaultDoor5.java](https://challenge-files.picoctf.net/c_fickle_tempest/e0273648f1276c71952d98ee6611263932f766fd288de297c1881a0e4fcd775c/VaultDoor5.java)
## Solucion
- descargamos el archivo ,java y lo abrimos con `nano`
- veo que en los comentario dice que esta codificado en base64
- hasta abajo veo esto:
```
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTM0JTMyJTYzJTM2JTM0JTMwJTM5JTYy";
```
- que de seguro es la bandera en base64 dividida en partes
- copio eso y le quito lo sobrante, lo pongo en cybershef y obtengo la bandera: **picoCTF{c0nv3rt1ng_fr0m_ba5e_64_42c6409b}**
## Notas

## Referencias
