## Reto
useless
## Descripcion
There's an interesting script in the user's home directoryThe work computer is running SSH. We've been given a script which performs some basic calculations, explore the script and find a flag.

## Solucion
- Trate de conectarme usando nc pero no servia usando eso
- Lei bien la descripcion y vi que debia usar ssh para entrar al servidor
- Trate de entrar usando este comando: `ssh saturn.picoctf.net -p 65306` pero no funcionaba cuando me pedia contraseña y me daba permiso denegado
- Le pregunte al chatgpt porque no servia y entendi que no me dejaba porque tenia que entrar como picoplayer y estaba intentando entrar con mi usuario que no existe en el servidor
- ahora uso el comando `ssh -p 65306 picoplayer@saturn.picoctf.net` y logro entrar con la contraseña que me dan
- aplico un ls para ver que encuentro y veo *useless*
- le aplico strings y no pasa nada, le aplico cat y veo que es solo un script para una calculadora simple
- le aplico un man y al final del manual esta la bandera **picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_4151}**

## Notas
- No entendia porque no podia conectarme al servidor hasta que chatgpt me dio el comando correcto, entonces entendi que necesitaba poner el `[ usuario ]@[ host ]`

## Referencias
https://chat.openai.com/chat
