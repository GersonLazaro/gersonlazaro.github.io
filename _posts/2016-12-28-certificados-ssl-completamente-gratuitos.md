---
layout: post
title:  "Certificados SSL completamente gratuitos"
date:   2016-12-28
description: "Los certificados SSL costosos o dificiles de configurar son cosa del pasado. En la actualidad, existe Let's Encrypt."
image: "/images/2016/12/certificado-ssl-gratuito.jpg"
---

###### ¿Qué es un certificado SSL?
> Un certificado SSL sirve para brindar seguridad al visitante de su página web, una manera de decirles a sus clientes que el sitio es auténtico, real y confiable para ingresar datos personales. (Tomado de <a href="https://www.certsuperior.com/QueesunCertificadoSSL.aspx" target="_blank">Certsuperior</a>)

En otras palabras, un certificado SSL cumple una función similar a la que un documento de identidad (cédula de ciudadania o similar) cumple en las personas. A través de mi cédula de ciudadanía, la república de Colombia certifica que yo soy quien digo ser. A través de un certificado SSL, una autoridad competente certifica que el sitio es auténtico y que se puede confiar en el. 

Ahora bien, ¿quien se encarga de certificar esto? Bueno, de hecho cualquiera puede hacerlo, tu puedes hacer tu propio certificado SSL y probarlo en tu localhost.  Sin embargo, estos certificados no serán aprobados por los navegadores y si lo colocas en un sitio en producción, seguramente tendrás un horrible aviso de seguridad cuando entres al sitio (así como una cédula expedida por mi mismo no será reconocida por la policía de mi país y tendré problemas legales). Para ellos existen entidades reconocidas que expiden sus certificados y los ofrecen generalmente bajo algún precio comercial por un tiempo definido.

###### ¿Como obtener un certificado SSL gratuito?

Patrocinada por los mas grandes de la industria tecnológica existe una Autoridad Certificadora que otorga certificados SSL completamente gratuitos por 90 días: <a href="https://letsencrypt.org/" target = "_blank">Let's Encrypt</a>. IMPORTANTE: Estos 90 dias no son un periodo de prueba o trial como ofrecen otras certificadoras, simplemente es el tiempo de vida del certificado, el cual puede renovarse al cumplir este tiempo para recibir 90 días gratuitos mas, y así indefinidamente. El proceso de renovación es muy simple, e incluso puede automatizarse para que no tengas que preocuparte por ello.

Entre los patrocinadores de Let's encrypt se encuentran Google Chrome, Linux, Facebook, Cisco, Shopify, Mozilla y HP Enterprise. Un respaldo de marcas mayores.

Para obtener un certificado de Let's Encrypt debes utilizar un cliente que utilice el protocolo ACME. Existen una multitud de clientes para diferentes sistemas operativos que puedes ver <a href="https://letsencrypt.org/docs/client-options/" target="_blank">aquí</a>. Se recomienda usar el cliente recomendado por la certificadora: <a href="https://certbot.eff.org/" target="_blank">CertBot</a>.

Hacer un tutorial en este punto sería algo complicado pues depende de tu sistema operativo y del software que utilices como servidor de aplicaciones web. Sin embargo, Certbot ha hecho un excelente tutorial para cada plataforma, al cual puedes acceder simplemente seleccionando tu servidor y sistema operativo en el sitio web oficial.
![Certbot let's Encrypt]
<span class="image center">
  <img src="/images/2016/12/certbot-lets-encrypt-ssl-gratis.png">
</span>


¿Que esperan para usarlo?

Enlaces:
<a href="https://letsencrypt.org/docs/client-options/" target="_blank">Let's Encrypt</a>
<a href="https://certbot.eff.org/" target="_blank">CertBot</a>

Nota final: Si eres estudiante, también puedes obtener un certificado SSL gratuito por un año entre otro montón de herramientas gracias a <a href="https://gersonlazaro.com/las-mejores-herramientas-para-desarrolladores-gratis-para-estudiantes/">Github para estudiantes</a>.