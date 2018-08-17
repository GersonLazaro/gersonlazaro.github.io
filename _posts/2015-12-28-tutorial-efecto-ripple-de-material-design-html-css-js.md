---
layout: post
title:  "TUTORIAL: Efecto Ripple de Material Design [HTML+CSS+JS]"
date:   2015-12-28
description: "Material Design ha traído nuevas ideas y componentes a nuestros diseños. El efecto Ripple es uno de los mas vistosos, y muy facil de lograr."
image: "/images/2015/12/material-buttons.png"
---

Sabemos de sobra las bondades que <a href="https://www.google.com/design/spec/material-design/introduction.html" target="_blank">Material Design</a> trae a nuestras aplicaciones, como sabemos también lo tedioso que puede ser lograrlo en HTML y CSS. Si bien existen varios frameworks de diseño que cubren por completo esta necesidad (como <a href="http://getmdl.io" target="_blank">Material Design Lite</a> y <a href="http://materializecss.com/" target="_blank">Materialize</a>), a veces necesitamos solo un pequeño elemento y no un framework completo. 

Hace unas horas necesitaba el efecto "Ripple" de Material Design al pulsar un botón. Buscando rápidamente en Google, encontré varias alternativas, todas ellas utilizando Jquery (y no, no me interesa importar Jquery cuando solo necesito un botón). Así que después de algunos intentos fallidos, decidí hacer el efecto a mano, con JavaScript y CSS. Para quienes no lo conocen o no asocian el nombre, este es el efecto Ripple (click a los elementos): 
<p data-height="330" data-theme-id="0" data-slug-hash="gPwJRz" data-default-tab="result" data-user="GersonLazaro" class='codepen'>See the Pen <a href='http://codepen.io/GersonLazaro/pen/gPwJRz/'>Ripple Effect</a> by Gerson Lazaro (<a href='http://codepen.io/GersonLazaro'>@GersonLazaro</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>


En primer lugar, hay que destacar que en el diseño material tenemos básicamente 3 tipos de botones: 

<span class="image center">
  <img src="/images/2015/12/botones-material.png">
</span>

Vamos a crear tres botones y un contenedor con una imagen (tambien a las imágenes podemos agregarle el efecto). En el html cada botón contendrá un DIV con clase ripple-container, que demarca los límites del efecto, y dentro de este div habrá un SPAN con clase ripple -effect encargado de desplegar el efecto como tal. La estructura HTML de los botones sería entonces:

<script src="https://gist.github.com/GersonLazaro/7aa7ff9e6c23c28e1aef.js"></script>

Para que los botones tengan el diseño deseado, vamos a añadir algo de css:

<script src="https://gist.github.com/GersonLazaro/42d0e5c1c211c9f2005a.js"></script>

Esto nos genera:

<span class="image center">
  <img src="/images/2015/12/botones-material-1.png">
</span>

Ahora si nos centramos en el efecto. A cada botón (y al bloque con la imagen) le hemos asignado un div interno con clase ripple-container. Este div debe ser transparente, pero ocupar la totalidad del tamaño del botón, lo cual no es muy difícil si lo ubicamos con posición absoluta. Del mismo modo, dentro de el div se encuentra un span con clase ripple-effect, al cual asignaremos una animación con keyframes, pero por defecto no será visible, y solo cuando se haga click sobre el elemento se disparará el evento que activa el span. Primero centrémonos en las propiedades css que harán funcionar el efecto:

<script src="https://gist.github.com/GersonLazaro/43c1e9134689adc74e50.js"></script>

Ahora si llega lo bueno: el javascript. Lo que haremos será capturar el click sobre el div ripple-container, ubicar el punto (x,y) dentro del botón en el cual se hizo el click, colocar ahí los valores top y left del span ripple-effect, y añadir la clase ripple-effect-animation al span para que la animación de los keyframes se active. Una vez la animación pase, de nuevo se quita esta clase, para que el botón siga funcionando (de lo contrario, el efecto solo funcionaria la primera vez). Veámoslo en código:

<script src="https://gist.github.com/GersonLazaro/d31bdcc1eb9d62bdfde4.js"></script>


El resultado final es el que ya he compartido al iniciar este post:

<p data-height="330" data-theme-id="0" data-slug-hash="gPwJRz" data-default-tab="result" data-user="GersonLazaro" class='codepen'>See the Pen <a href='http://codepen.io/GersonLazaro/pen/gPwJRz/'>Ripple Effect</a> by Gerson Lazaro (<a href='http://codepen.io/GersonLazaro'>@GersonLazaro</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

Todo el código utilizado puedes descargarlo también desde [Github Gist](https://gist.github.com/GersonLazaro/d32bcbe009a95d8f89b2).

Cualquier duda puedes dejarla en los comentarios. Hasta la próxima!