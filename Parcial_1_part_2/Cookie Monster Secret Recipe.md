
## Reto
### Cookie Monster Secret Recipe
## Descripcion
Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:61453/) and good luck

## Solucion
- abrimos el portal y hay un formulario de usuario y contraseña
- ponemos datos dummy y fallamos pero nos dicen si ya checamos toda la pagina
- si vemos la cookie vemos que es como un codigo cifrado
- si lo ponemos en burpsuite en decoder nos manda un regresa un texto en base64
- cuando ponemos ese texto en cybershef nos regresa la bandera: **picoCTF{c00k1e_m0nster_l0ves_c00kies_C430AE20}**
## Notas

## Referencias
[picoCTF Web Exploitation: Cookie Monster Secret Recipe | by Kamal S | Medium](https://medium.com/@Kamal_S/picoctf-web-exploitation-cookie-monster-secret-recipe-4c1776da9251)
