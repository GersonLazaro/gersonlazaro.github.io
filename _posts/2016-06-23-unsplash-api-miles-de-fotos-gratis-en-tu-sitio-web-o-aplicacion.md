---
layout: post
title:  "Unsplash API: Miles de fotos gratis en tu sitio web o aplicación"
date:   2016-06-23
description: "Las mejores fotos de todo el internet, libres para usar en tus proyectos personales o comerciales con solo un par de clics."
image: "/images/2016/06/camara-imagenes-gratis.jpg"
---

Ya en alguna ocasión había compartido <a href="https://gersonlazaro.com/imagenes-gratis-y-libres-para-uso-personal-yo-profesional/" target="_blank">una lista de sitios para descargar imágenes libres de derechos de autor</a>. En aquella época, colocaba de primero en la lista a Unsplash, indicando que era mi sitio favorito, y que por aquel entonces era una simple cuenta de tumblr que compartía imágenes gratuitas de alta calidad.

Pues ha crecido bastante <a href="http://www.unsplash.com" target="_blank">unsplash</a> en este tiempo, y ahora es algo mil veces mejor. Se ha convertido en una completa plataforma con mas de 40 mil fotógrafos, y una infinidad de fotos de la mas grande calidad, completamente gratis y libres. No he encontrado el dato oficial de cuantas fotos tienen actualmente, pero lo que si estoy seguro es que el titulo "miles de fotos" se queda corto. 

Pero eso no es lo mejor: ahora cuenta con una completa API para utilizar sus recursos en tus aplicaciones sin problemas. O mejor, cuenta con dos API's. Una API simple, sencilla y perfecta para obtener imágenes directamente en tu sitio web o aplicación sin mayor dificultad, y una API JSON completa para proyectos mas complejos y con mas funcionalidades. 

Vamos a explicar la API simple, que sin duda es mas que suficiente para la gran mayoría de proyectos. Recibe el nombre de <a href="https://source.unsplash.com/" target="_blank">Unsplash Source</a> y permite embeber imágenes de unsplash directamente con solo un link. Veamos algunos ejemplos:

##### Imagen Aleatoria
Para insertar una imagen aleatoria de alta calidad, simplemente usa el siguiente link. 

`https://source.unsplash.com/random`

Cada vez que recargues, cargará una imagen diferente. A continuación, un ejemplo: 

<span class="image center">
  <img src="https://source.unsplash.com/random/800x600">
</span>

##### Imagen por una determinada categoría
Tenemos 6 categorías predefinidas sobre las cuales podemos cargar imágenes. Estas categorías son: buildings (construcciones), food (comida), nature (naturaleza), people (gente), technology (tecnología) y objects (objetos). Para solicitar una imagen de una categoría especifica, simplemente utilizamos: 

`https://source.unsplash.com/category/{NOMBRE_DE_LA_CATEGORIA}`

Por ejemplo:

`https://source.unsplash.com/category/nature/`

Devuelve una imagen diferente de la categoría naturaleza cada vez que recargue:

<span class="image center">
  <img src="https://source.unsplash.com/category/nature/800x600">
</span>

##### Imagen de una colección
Unsplash ahora cuenta con colecciones, un concepto similar al de "álbum" en facebook. Si quieres tomar imágenes únicamente de una colección, que bien puede ser creada por otro usuario o por ti mismo, simplemente necesitas saber el ID de la colección. El link quedaría:

`https://source.unsplash.com/collection/{ID DE LA COLECCIÓN}`

Por ejemplo, una de mis colecciones favoritas es <a href="https://unsplash.com/collections/881002/feng-shui-inspired" target="_blank">"Feng Shui Inspired"</a> de Bettina Kohl. Abriendo el link puedo ver que su ID es 881002. Por lo tanto para tomar una foto aleatoria de esta colección, simplemente necesito:

`https://source.unsplash.com/collection/881002`

Que me da como resultado:

<span class="image center">
  <img src="https://source.unsplash.com/collection/881002/800x600">
</span>

En todos los ejemplos previos tendremos una imagen diferente cada vez que recargues. Si en vez de eso, quieres la misma imagen, tienes 3 opciones:

##### Foto fija estática:
Siempre la misma imagen, adjuntando su ID en el link:

`https://source.unsplash.com/{PHOTO ID}`

Por ejemplo:

`https://source.unsplash.com/umchkHwkdyM`

Cargará siempre la siguiente imagen:

<span class="image center">
  <img src="https://source.unsplash.com/umchkHwkdyM/800x600">
</span>

##### Foto fija diaria
Todos los días tendrás una imagen diferente, pero si recargas en el mismo día, seguirás teniendo la misma imagen todas las veces:

`https://source.unsplash.com/daily`

Que muestra:

<span class="image center">
  <img src="https://source.unsplash.com/800x600/daily">
</span>

##### Foto fija semanal
Todas las semanas tendrás una imagen diferente, pero durante la semana, seguirás teniendo la misma imagen todas las veces:

`https://source.unsplash.com/weekly`

Que muestra:

<span class="image center">
  <img src="https://source.unsplash.com/800x600/weekly">
</span>

Tanto a la imagen diaria como a la semanal puedes añadirle una categoría, como por ejemplo:

`https://source.unsplash.com/category/technology/weekly`

ó:

`https://source.unsplash.com/category/people/daily`

##### Imagen de lo que tu quieras!

Si quieres una imagen de un tema muy en especifico, PUEDES INDICARLO!. Tu escribes las palabras claves, y Unsplash busca una imagen aleatoria relacionada con estas palabras claves. IMPORTANTE: Unsplash está en inglés, así que preferiblemente los tags deben estar en ese idioma.

`https://source.unsplash.com/random/?{PALABRA_CLAVE1},{PALABRA_CLAVE2}...`

Puedes añadir todas las palabras clave que quieras, separadas por comas. Por ejemplo:

`https://source.unsplash.com/random/?river,park` debería devolver una imagen relacionada a "río" y "parque". Dado que la imagen que verás es aleatoria, no puedo asegurar que la relación es exacta, pero al menos contendrá estos tags.

<span class="image center">
  <img src="https://source.unsplash.com/random/800x600/?river,park">
</span>

##### Tamaño de la imagen
Si lo deseas, también puedes indicar en que tamaño recibirás la imagen, de manera muy simple. De hecho, todas las imágenes que han aparecido de ejemplo en este post, están en 800x600. Simplemente basta con agregas las dimensiones en el link (puede aplicarse a cualquiera de los ejemplos vistos):

`https://source.unsplash.com/random/800x600`

`https://source.unsplash.com/category/nature/800x600`

`https://source.unsplash.com/collection/240395/800x600`

`https://source.unsplash.com/800x600/daily`

`https://source.unsplash.com/random/800x600/?river,park`

##### Licencia de las imágenes

Todas las fotos publicads en Unsplash están licenciadas bajo <a href="https://creativecommons.org/publicdomain/zero/1.0/deed.es" target="_blank">Creative Commons Zero</a> lo cual te permite copiar, modificar, distribuir y usar las fotos libremente, para propósitos personales y/o comerciales, sin necesidad de pedir permiso o proveer atribución al fotógrafo o a la plataforma.
