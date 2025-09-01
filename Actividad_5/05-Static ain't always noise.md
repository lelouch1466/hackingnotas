## Reto
Static ain't always noise
## Descripcion
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static)? This [BASH script](https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh) might help!

## Solucion
- Descargo el stsatic y el script que me dan primero
- Hago un cat al script para ver que es y me doy cuenta que es un script
- No se como correrlo y darle el archivo static para descubrir la bandera
- Use chatgpt para que me diera los comandos para abrir un script
- Para abrir un script se usa `./[nombre script] [argumentos]`
- Trato de correrlo como `./ltdis.sh static` pero me sale permiso denegado
- Para que pueda correr debo darle permiso de correr primero con `chmod +x ltdis.sh`
- Ahora con permiso corro el script y decodifica static y me da un .txt nuevo, uso cat sobre el texto y encuentro la bandera: **picoCTF{d15a5m_t34s3r_f5aeda17}**

## Notas
- Ahora se como correr un script y darles el permiso para correr para desafios futuros

## Referencias
https://chat.openai.com/chat
