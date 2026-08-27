# demos.unonuevecr.com

Portada de demostraciones de UNONUEVE. Cuatro casos de ejemplo con datos inventados, cada uno
detrás de un código de acceso.

| Ruta | Caso | Código |
|---|---|---|
| `odontologia/` | Clínica Dental del Oeste | `DENTAL-19` |
| `estetica/` | Clínica Novara | `ESTETICA-19` |
| `bufete/` | Quirós Madrigal & Asociados | `LEGAL-19` |
| `joyeria/` | Maracuyá Jewels | `JOYAS-19` |

También se puede mandar el enlace con el código adentro y entra directo:
`.../odontologia/?c=DENTAL-19`

## Estado del dominio

Mientras no exista el registro `CNAME demos → unonuevecr.github.io.` en Google Cloud DNS
(proyecto `unonueve`), el sitio vive en la URL de GitHub Pages. Para pasarlo al dominio propio:
crear el archivo `CNAME` con `demos.unonuevecr.com` y volver a publicar.

## Cómo está hecho el candado

Cada panel va **cifrado con AES-256-GCM** dentro de su propia página. La llave se deriva del código
con PBKDF2 (150.000 vueltas, SHA-256). Sin el código no hay nada que leer: en el archivo solo hay
texto cifrado. No es un `if` de JavaScript que se pueda saltar mirando el código fuente.

## Cómo se regenera

El sitio se arma con `build_demos_site.py` (respaldado en la carpeta Demostraciones del vault).
Lee los paneles ya construidos, los envuelve como documento completo, los cifra y escribe estas
carpetas. Los enlaces son relativos, así que el sitio funciona igual en la raíz de un dominio
propio que bajo `/unonueve-demos/`.

Los datos de las cuatro demostraciones son inventados. No corresponden a ninguna persona ni empresa real.
