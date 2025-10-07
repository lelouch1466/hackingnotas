
## Reto
Specialer

## Descripcion
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.

Additional details will be available after launching your challenge instance.

## Solucion
- al entrar al sistema trato un ls pero veo que no funciona
- trato de hacer ./* y encuentra un directorio llamado abra
- ahora hago `./*/*` y encuentro cadabra.txt y presiento que ahi esta la bandera
- como no tengo `cat` trato el mismo truco que en SansAlpha usando base...pero no tengo base64 :v
- para saber que comandos tengo presiono TAB 2 veces seguidas y ahi encuentro que puedo usar
- veo que puedo usar echo y cd
- como tengo echo lo puedo usar para imprimir en consola archivo como un cat usando
```
echo$(<archivo)
```
- entonces lo abro lo que quiero con `echo $(<./abra/cadabra.txt)` pero no hay nada
- ahora usando el mismo truco de presionar TAB 2 veces, pongo cd y tab tab
- me salen todos los directorios como en un ls
- encuentro otros 2 directorios: ala/ sim/
- entro a ala, de nuevo cd tab tab y veo otros 2 .txt: kazam y mode
- al abrir `echo $(>ala/kazam.txt)` obtengo la bandera: **picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_838b49d1}**

## Notas

## Referencias
[Pico CTF (Specialer) | j053's playground](https://josephkimiri.github.io/posts/Specialer/)