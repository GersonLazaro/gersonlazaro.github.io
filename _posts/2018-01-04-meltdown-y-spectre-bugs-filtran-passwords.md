---
layout: post
cover: 'content/images/2018/01/meltdown-y-spectre.png'
title: 'Meltdown y Spectre: Bugs en computadores modernos que filtran contraseñas e información sensible'
description: 'Meltdown y Spectre: Bugs en computadores modernos que podrían filtrar contraseñas e información sensible aprovechando vulnerabilidades existentes en diversos procesadores.'
date:   2018-01-04 12:12:12
categories: tech seguridad
navigation: True
---

> Este artículo es una traducción de la información original en inglés publicada <a href="https://meltdownattack.com" target="_blank">aquí</a>. Por tanto, puede contener información técnica. Si no desea profundizar en estos tecnicismos, la recomendación es simple: No entre en pánico, y mantenga su sistema operativo actualizado.

Meltdown y Spectre se aprovechan de vulnerabilidades críticas en procesadores modernos. Estos errores de hardware permiten a los programas robar datos que están siendo procesados por el computador. Si bien los programas normalmente no tienen permiso para leer datos de otros programas, un programa malicioso puede explotar Meltdown o Spectre para obtener información secreta guardada en la memoria de otros programas en ejecución. Esto podría incluir sus contraseñas almacenadas en un administrador de contraseñas o un navegador, sus fotos personales, correos electrónicos, mensajes instantáneos e incluso documentos confidenciales críticos de empresas.

Meltdown y Spectre trabajan en computadoras personales, dispositivos móviles y en la nube. Dependiendo de la infraestructura del proveedor de la nube, podría ser posible robar datos de otros clientes.

### Meltdown

![](/content/images/2018/01/meltdown.png)

Meltdown rompe el aislamiento fundamental entre las aplicaciones del usuario y el sistema operativo. Este ataque permite que un programa acceda a la memoria y, por lo tanto, también a los datos secretos de otros programas y del sistema operativo.

Si su computadora tiene un procesador vulnerable y ejecuta un sistema operativo no parcheado, no es seguro trabajar con información confidencial (existe la posibilidad de filtrado de la información). Esto se aplica tanto a las computadoras personales como a la infraestructura en la nube. Afortunadamente, ya existen parches de software contra Meltdown.

### Spectre

![](/content/images/2018/01/spectre.png)

Spectre rompe el aislamiento entre diferentes aplicaciones. Esto permite a un atacante engañar a programas sin errores en su diseño, desarrollado con las mejores prácticas, para filtrar sus datos secretos. De hecho, los controles de seguridad de dichas mejores prácticas en realidad aumentan las posibilidades de ataque y pueden hacer que las aplicaciones sean más susceptibles a Spectre.

Spectre es más difícil de explotar que Meltdown, pero también es más difícil de mitigar. Sin embargo, es posible evitar exploits conocidos específicos basados en Spectre a través de parches de software.

##### ¿Este error me afecta?

Sin duda, sí.

##### ¿Puedo detectar si alguien ha explotado Meltdown o Spectre en mi contra?

Probablemente no. La explotación no deja ningún rastro en los archivos de registro tradicionales.

##### ¿Mi antivirus puede detectar o bloquear este ataque?

Aunque en teoría es posible, en la práctica es poco probable. A diferencia del malware habitual, Meltdown y Spectre son difíciles de distinguir de las aplicaciones comunes. Sin embargo, su antivirus puede detectar malware que usa estos bugs comparando sus archivos binarios una vez que se hacen conocidos.

##### ¿Qué información se puede filtrar?

Si su sistema se ve afectado, un exploit que explote estas vulnerabilidades podría leer el contenido de la memoria de su computadora. Esto puede incluir contraseñas y datos confidenciales almacenados en el sistema.

##### ¿Meltdown o Spectre ya han sido aprovechados por atacantes maliciosos?

No lo sabemos.

##### ¿Hay una solución?

Hay parches contra Meltdown para Linux (<a href="https://lwn.net/Articles/738975/" target="_blank">KPTI (anteriormente KAISER))</a>, Windows y OS X. También se está trabajando para fortalecer el software contra la futura explotación de Spectre (<a href="http://lists.llvm.org/pipermail/llvm-commits/Week-of-Mon-20180101/513630.html" target="_blank">parche LLVM</a>).

##### ¿Qué sistemas se ven afectados por Meltdown?

Los computadores de escritorio, portátiles y en la nube podrían verse afectadas por Meltdown. Más técnicamente, cada procesador Intel que implemente la ejecución especulativa se ve potencialmente afectado, es decir, todos sus procesadores desde 1995 (excepto Intel Itanium e Intel Atom antes de 2013). Actualmente, solo se ha verificado Meltdown en procesadores Intel. Por el momento, no está claro si los procesadores ARM y AMD también se ven afectados por Meltdown.

##### ¿Qué sistemas se ven afectados por Spectre?

Casi cualquier equipo puede ser afectado por Spectre: Computadores de escritorio, portátiles, servidores en la nube y smartphones. Más específicamente, todos los procesadores modernos capaces de mantener muchas instrucciones en vuelo son potencialmente vulnerables. En particular, se han verificado Spectre en procesadores Intel, AMD y ARM.

##### ¿Qué proveedores en la nube se ven afectados por Meltdown?

Proveedores de nube que usan CPU Intel y paravirtualización Xen sin aplicar parches. Además, los proveedores en la nube sin virtualización de hardware real, que dependen de contenedores que comparten un kernel, como Docker, LXC u OpenVZ se ven afectados.

##### ¿Cuál es la diferencia entre Meltdown y Spectre?

Meltdown rompe el mecanismo que impide que las aplicaciones accedan arbitrariamente a la memoria del sistema. En consecuencia, las aplicaciones pueden acceder a la memoria del sistema. Spectre engaña a otras aplicaciones para acceder a ubicaciones arbitrarias en su memoria. Ambos ataques usan canales laterales para obtener la información de la ubicación de la memoria a la que se accede. Para una discusión más técnica, puedes leer los artículos (<a href="https://meltdownattack.com/meltdown.pdf" target="_blank">Meltdown</a> and <a href="https://spectreattack.com/spectre.pdf" target="_blank">Spectre</a>).

##### ¿Por qué se llama Meltdown?

El error básicamente funde los límites de seguridad que normalmente son aplicados por el hardware (Fundir en inglés traduce Melt, de allí el nombre Meltdown).

##### ¿Por qué se llama Spectre?

El nombre se basa en la causa raíz, la ejecución especulativa. Como no es fácil de solucionar, nos perseguirá durante bastante tiempo (El nombre en español traduce espectro, que puede entenderse como fantasma, de allí la explicación).

##### ¿Hay más información técnica sobre Meltdown y Spectre?

Sí, hay un <a href="https://meltdownattack.com/meltdown.pdf" target="_blank">trabajo académico</a> y una <a href="http://blog.cyberus-technology.de/posts/2018-01-03-meltdown.html" target="_blank">entrada de blog</a> sobre Meltdown, y un <a href="https://spectreattack.com/spectre.pdf" target="_blank">trabajo académico</a> sobre Spectre. Además, hay una <a href="https://googleprojectzero.blogspot.co.at/2018/01/reading-privileged-memory-with-side.html" target="_blank">entrada de blog</a> de Google Project Zero sobre ambos ataques.

##### ¿Qué son CVE-2017-5753 y CVE-2017-5715?

CVE-2017-5753 y CVE-2017-5715 son las referencias oficiales de Spectre. CVE es el Estándar para Nombres de Vulnerabilidades de Seguridad de la Información mantenido por MITRE.

##### Que es CVE-2017-5754?

CVE-2017-5754 es la referencia oficial de Meltdown. CVE es el Estándar para Nombres de Vulnerabilidades de Seguridad de la Información mantenido por MITRE.

##### ¿Quién descubrió Meltdown?

Meltdown fue descubierto y reportado de forma independiente por tres equipos:

* Jann Horn (Google Project Zero),
* Werner Haas y Thomas Prescher (Cyberus Technology),
* Daniel Gruss, Moritz Lipp, Stefan Mangard y Michael Schwarz (Universidad Tecnológica de Graz)

##### ¿Quién descubrió Spectre?

Spectre fue descubierto y reportado de forma independiente por dos personas:

Jann Horn (Google Project Zero) y Paul Kocher en colaboración con Daniel Genkin (Universidad de Pensilvania y Universidad de Maryland), Mike Hamburg (Rambus), Moritz Lipp (Universidad Tecnológica de Graz) y Yuval Yarom (Universidad de Adelaida y Data61).

> Artículo técnico sobre Meltdown: <a href="https://meltdownattack.com/meltdown.pdf" target="_blank">Clic aquí</a>

> Artículo técnico sobre Spectre: <a href="https://spectreattack.com/spectre.pdf" target="_blank">Clic aquí</a>

> Los logos de Meltdown y Spectre usados en este artículo fueron diseñados por <a href="https://vividfox.me/" target="_blank">Natascha Eibl</a> y se comparte bajo licencia <a href="http://creativecommons.org/publicdomain/zero/1.0/" target="_blank">Creative Commons Zero</a>.