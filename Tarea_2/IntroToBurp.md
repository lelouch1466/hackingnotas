
## Reto
 IntroToBurp

## Descripcion
Try [here](http://titan.picoctf.net:51984/) to find the flag
## Solucion
- en kali abro la pagina que me dan y contiene un formulario
- despues de llenarlo con datos dummy, me pregunta por una OTP (one time password)
- al poner cualquier cosa solo me sale otp invalido
- abro foxyproxy y burpsuite para interceptar el request al momento de poner el otp
- al interceptarlo lo envio al repeater donde en la linea que dice 'otp=[algo]' la borro completamente y pongo cualquier caracter en su lugar, al hacer esto la respuesta que me da es la bandera **picoCTF{#0TP_Bypvss_SuCc3$S_b3fa4f1a}**

## Notas

## Referencias
[picoCTF Web Exploitation: IntroToBurp | by Kamal S | Medium](https://medium.com/@Kamal_S/picoctf-web-exploitation-introtoburp-a2b50bf8e985)
