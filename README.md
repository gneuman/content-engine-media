# guest-podcasting-media

Imágenes y video listos para publicar, de las **fuentes** procesadas con
[guest-podcasting](https://github.com/gneuman/guest-podcasting). Una fuente
puede ser un episodio de podcast, un dev-log de una promoción a producción, un
blog o una idea — todas producen media aquí de la misma forma.

Este repo existe por una razón concreta: publicar una imagen en LinkedIn o
Instagram vía API necesita una **URL pública**, y el repo de trabajo es privado.
Aquí vive solo lo que de todos modos va a salir a redes.

## Qué hay aquí

```
<fuente>/<pieza>/media-01.png
<fuente>/<pieza>/media-01.jpeg
<fuente>/<pieza>/*.mp4
<fuente>/<pieza>/thumbnail.png
```

Cada carpeta corresponde a una publicación: una quote, un carrusel, una
infografía, un diagrama, un video. El primer nivel es el slug de la fuente
(arbitrario), así que la estructura no asume nada sobre de dónde vino.

## Qué NO hay aquí

Transcripciones, frames del video original, especificaciones de curaduría,
fuentes HTML editables, perfil de voz, scripts. Todo eso se queda en el repo
privado.

## Cómo se sirve

Vía [jsDelivr](https://www.jsdelivr.com/), gratis y con CDN global:

```
https://cdn.jsdelivr.net/gh/gneuman/guest-podcasting-media@main/<fuente>/<pieza>/media-01.png
```

Para una pieza ya programada o publicada conviene fijar el commit en vez de
`@main`, porque jsDelivr cachea de forma agresiva y una pieza re-renderizada
seguiría sirviendo el archivo anterior:

```
https://cdn.jsdelivr.net/gh/gneuman/guest-podcasting-media@<sha>/<fuente>/<pieza>/media-01.png
```

## Cómo se actualiza

No a mano. Desde el repo privado:

```bash
python scripts/publicar_assets.py <fuente>
python scripts/publicar_assets.py --todos --dry-run    # ver antes de aplicar
```

El script copia la media de las piezas en estado `listo` o `aprobado`, hace
push aquí, y escribe la URL resultante en el `publish.json` de cada pieza.

## Derechos

Contenido de [Gabriel Neuman](https://www.gabrielneuman.com).
