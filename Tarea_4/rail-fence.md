
## Reto
### rail-fence
## Descripcion
A type of transposition cipher is the rail fence cipher, which is described [here](https://en.wikipedia.org/wiki/Rail_fence_cipher). Here is one such cipher encrypted using the rail fence with 4 rails. Can you decrypt it?Download the message [here](https://artifacts.picoctf.net/c/189/message.txt).Put the decoded message in the picoCTF flag format, `picoCTF{decoded_message}`.
## Solucion
- nos estan diciendo que existe el cifrado rail fence y como decifrarlo
- el mensaje que nos dan es:
```
Ta _7N6D8Dhlg:W3D_H3C31N__387ef sHR053F38N43DFD i33___N6
```
- si lo ponemos en cybershef y buscamos `rail fence decode` y ponemos 4 en la llave nos regresa la bandera:
```
The flag is: WH3R3_D035_7H3_F3NC3_8361N_4ND_3ND_83F6D8D7
```
## Notas

## Referencias
