
## Reto
### Bookmarklet

## Descripcion
Why search for the flag when I can make a bookmarklet to print it for me?Browse [here](http://titan.picoctf.net:52262/), and find the flag!

## Solucion
- al abrir la pagina me dice que ya recivi la bandera
- hay un cuadro de texto con codigo de javascript que se copia automaticamente
- al inspeccionar los elementos de la pagina coy a consola y trato de pegar el codigo que me dieron
```
        javascript:(function() {
            var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓ¡ÒÅ¤í";
            var key = "picoctf";
            var decryptedFlag = "";
            for (var i = 0; i < encryptedFlag.length; i++) {
                decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
            }
            alert(decryptedFlag);
        })();
    
```
- primero tengo que poner "allow pasting" y ya me deja poner el codigo, le doy enter y me da la bandera en una notificacion del navegador: **picoCTF{p@g3_turn3r_0148cb05}**

## Notas
- trate de pegar el codigo en consula antes de ver una solucion pero como decia que no era seguro hacer eso y que mi lap podria explotar mejor revice un writeup

## Referencias
[picoCTF Web Exploitation: Bookmarklet - Kamal S - Medium](https://medium.com/@Kamal_S/picoctf-web-exploitation-bookmarklet-9e7d72c97f96)