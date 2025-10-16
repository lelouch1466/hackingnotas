
## Reto
Riddle Registry
## Descripcion
#### Description

Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered.Find the PDF file here [Hidden Confidential Document](https://challenge-files.picoctf.net/c_saffron_estate/8fc7f4db4cd616afa42099769749bbf3620925ed4ee7d2037ffdbd525aa14dc6/confidential.pdf) and uncover the flag within the metadata.

## Solucion
- al abrir el pdf hay un documento con lineas tachadas pero no dice nada interesante
- lo abro en notepad para buscar por pico pero tampoco nada
- al hacer `exiftool` al archivo para ver su metadata veo que en el autor hay un cifrado de base64, al usar cybershef para decifrarlo obtengo la bandera: **picoCTF{puzzl3d_m3tadata_f0und!_c8f91d68}**
## Notas

## Referencias
[From Base64 - CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Base64\('A-Za-z0-9%2B/%3D',true,false\)&input=Y0dsamIwTlVSbnR3ZFhwNmJETmtYMjB6ZEdGa1lYUmhYMll3ZFc1a0lWOWpPR1k1TVdRMk9IMD0&ieol=CRLF&oeol=CRLF)