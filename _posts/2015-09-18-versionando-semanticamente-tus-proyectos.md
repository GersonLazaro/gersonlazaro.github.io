---
layout: post
cover: 'content/images/2015/09/versionado-semantico.jpg'
title: Versionando semánticamente tus proyectos de software
date:   2015-09-18 06:06:00
categories: programacion tech web
navigation: True
---

Según wikipedia, *"El versionado de software es el proceso de asignación de un nombre, código o número único, a un software para indicar su nivel de desarrollo."*

Si bien el versionado de un software puede ser definido por el propio equipo de trabajo de la manera en que lo considere conveniente, existen estándares que definen reglas que de cara al usuario dan una noción clara del estado actual de desarrollo, de cara al equipo refleja una mejor organización y estabilidad, y mas importante aún, de cara al producto de software permiten establecer claridad en cuanto a la dependencia e interoperabilidad entre paquetes y versiones. 

A continuación se presenta el sistema de versionado semántico, ampliamente extendido y usado en la actualidad por proyectos de software de todos los tipos y magnitudes.

> Definido y publicado originalmente por <a href="http://tom.preston-werner.com/" target="_blank">Tom Preston-Werner</a> en <a href="http://semver.org/" target="_blank">Semver.org</a> bajo licencia <a href="http://creativecommons.org/licenses/by/3.0/" target="_blank">Creative Commons 3.0</a>.

##### Resumen

Dado un número de versión MAYOR.MENOR.REVISIÓN, incrementar:

* Versión MAYOR cuando se realizan cambios de API incompatibles con la versión anterior,
* Versión MENOR cuando se agrega nueva funcionalidad compatible con versiones anteriores, y
* Versión de REVISIÓN al realizar correcciones de errores, compatibles con versiones anteriores.

Etiquetas adicionales para pre-lanzamiento y metadatos de la versión están disponibles como extensiones al formato MAYOR.MENOR.REVISIÓN.

##### Introducción
En el mundo de la gestión de software existe el temor de caer en algún momento en el llamado “infierno de las dependencias”. Mientras más crece tu sistema y mientras más paquetes integras en tu software, más probable es que te encuentres, un día, en este pozo de la desesperación.

En sistemas con muchas dependencias, publicar nuevas versiones de un paquete puede transformarse rápidamente en una pesadilla. Si las especificaciones de dependencia son muy estrictas está el peligro del bloqueo de versiones (la imposibilidad de actualizar un paquete sin tener que actualizar todos los que dependen de este). Si las dependencias se especifican de manera muy amplia, inevitablemente caerás en promiscuidad de versiones (asumir más compatibilidad de lo razonable con versiones futuras). El infierno de las dependencias es donde te encuentras cuando el bloqueo de versiones o la promiscuidad de versiones te impiden avanzar en tu proyecto de manera fácil y segura.

Como solución a este problema, propongo un set simple de reglas y requerimientos que dictan cómo asignar y cómo aumentar los números de versión. Para que este sistema funcione, tienes que declarar primero un API pública. Esto puede consistir en documentación o ser explicitado en el código mismo. De cualquier forma, es importante que esta API sea clara y precisa. Una vez que identificaste tu API pública, comunicas cambios a ella con aumentos específicos al número de versión. Considera un formato de versión del tipo X.Y.Z (Major.Minor.Patch) Los arreglos de bugs que no cambian el API incrementan el patch, los cambios y adiciones que no rompen la compatibilidad de las dependencias anteriores incrementan el minor, y los cambios que rompen la compatibilidad incrementan el major.

Yo llamo a este sistema “Versionamiento Semántico”. Bajo este esquema, los números de versión y la forma en que cambian entregan significado del código que está detrás y lo que fue modificado de una versión a otra.

##### Especificación de Versionamiento Semántico 
1. El software que use Versionamiento Semántico DEBE declarar una API pública. Esta API puede ser declarada en el código mismo o existir en documentación estricta. De cualquier manera, debería ser precisa y completa.

2. Un número normal de versión DEBE tomar la forma X.Y.Z donde X, Y, y Z son enteros no negativos. X es la versión “mayor”, Y es la versión “menor”, y Z es la versión “revisión”. Cada elemento DEBE incrementarse numéricamente en incrementos de 1. Por ejemplo: 1.9.0 -> 1.10.0 -> 1.11.0.

3. Una vez que un paquete versionado ha sido liberado (release), los contenidos de esa versión NO DEBEN ser modificadas. Cualquier modificación DEBE ser liberada como una nueva versión.

4. La versión mayor en cero (0.y.z) es para desarrollo inicial. Cualquier cosa puede cambiar en cualquier momento. El API pública no debiera ser considerada estable.

5. La versión 1.0.0 define el API pública. La forma en que el número de versión es incrementado después de este release depende de esta API pública y de cómo esta cambia.

6. La versión revisión Z (x.y.Z - x > 0) DEBE incrementarse cuando se introducen solo arreglos compatibles con la versión anterior. Un arreglo de bug se define como un cambio interno que corrige un comportamiento erróneo.

7. La versión menor Y (x.Y.z - x > 0) DEBE ser incrementada si se introduce nueva funcionalidad compatible con la versión anterior. Se DEBE incrementar si cualquier funcionalidad de la API es marcada como obsoleta. PUEDE ser incrementada si se agrega funcionalidad o arreglos considerables al código privado. Puede incluir cambios de nivel de revisión. La versión de revisión DEBE ser reiniciada a 0 cuando la versión menor es incrementada.

8. La versión mayor X (X.y.z - X > 0) DEBE ser incrementada si cualquier cambio no compatible con la versión anterior es introducida a la API pública. PUEDE incluir cambios de niver menor y/o revisión. Las versiones revisión y menor DEBEN ser reiniciadas a 0 cuando se incrementa la versión mayor.

9. Una versión pre-lanzamiento PUEDE ser representada añadiendo un guión y una serie de identificadores separados por puntos inmediatamente después de la versión de revisión. Los identificadores DEBEN consistir solo de caracteres ASCII alfanuméricos y el guión [0-9A-Za-z-]. Los identificadores NO PUEDEN ser vacios. Los identificadores numéricos NO DEBEN incluir ceros a la izquierda. Las versiones Pre-lanzamiento tienen una menor precedencia que la versión normal asociada. Ejemplos: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92.

10. Los metadatos de la versión PUEDEN ser representados adjuntando un signo más y una serie de identificadores separados por puntos inmediatamente después de la versión revisión o la pre-lanzamiento. Los identificadores DEBEN consistir sólo de caracteres ASCII alfanuméricos y el guión [0-9A-Za-z-]. Los metadatos de la versión DEBIERAN ser ignorados cuando se intenta determinar precedencia de versiones. Luego, dos paquetes con la misma versión pero distinta metadatos de versión se consideran la misma versión. Ejemplos: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85.

11. La precedencia DEBE ser calculada separando la versión en mayor, menor, revisión e identificadores pre-lanzamiento en ese orden (Los metadatos de la versión no figuran en la precedencia). Las versiones mayor, menor, y revisión son siempre comparadas numéricamente. La precedencia de pre-lanzamiento DEBE ser determinada comparando cada identificador separado por puntos de la siguiente manera: los identificadores que solo consisten de números son comparados numéricamente y los identificadores con letras o guiones son comparados de acuerdo al orden establecido por ASCII. Los identificadores numéricos siempre tienen una precedencia menor que los no-numéricos. Ejemplo: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.

##### ¿Por qué usar Versionamiento Semántico?

Esta no es una idea nueva o revolucionaria. De hecho, probablemente ya haces algo cercano hoy en día. El problema es que “cercano” no es suficientemente bueno. Sin un acuerdo en algún tipo de especificación formal, los números de versiones son esencialmente inútiles para el manejo de dependencias. Al darle un nombre y una definición clara a las ideas expresadas arriba, se hace fácil comunicar tus intenciones a los usuarios de tu software. Una vez que estas intenciones son claras y flexibles (pero no demasiado flexibles) finalmente se pueden hacer especificaciones de dependencias.

Un ejemplo simple puede demostrar como el Versionamiento Semántico puede ayudar a que el infierno de dependencias quede en el pasado. Considera una librería llamada "CarroBomba" que requiere de un paquete semánticamente versionado llamado “Escalera”. En el momento en que se crea CarroBomba, Escalera está en su versión 3.1.0. Como CarroBomba usa algunas de las funcionalidades que recién se estrenaron en la versión 3.1.0, puedes tranquilamente definir la dependencia de Escalera como mayor o igual a 3.1.0, pero menor a 4.0.0. Ahora, cuando la versión 3.1.1 y 3.2.0 de Escalera sean liberadas, puedes usarlas en tu sistema de versionamiento de paquetes sabiendo que serán compatibles con el software dependiente.

Como desarrollador responsable que eres, claro, querrás verificar que cualquier actualización de paquete funcione como se anunció. El mundo real es complejo; no hay nada que podamos hacer salvo estar atentos. Lo que puedes hacer es dejar que el Versionamiento Semántico te provea de una manera sana de liberar y actualizar paquetes sin tener que entregar nuevas versiones de tus paquetes dependientes, ahorrándote tiempo y molestias.

Si todo esto suena deseable, todo lo que tienes que hacer para comenzar usando Versionamiento Semántico es declarar que lo estás haciendo y seguir las reglas. Haz un link <a href="http://semver.org/" target="_blank">a este sitio</a> desde tu README para que otros conozcan las reglas y se puedan beneficiar de ellas.

> Definido y publicado originalmente por <a href="http://tom.preston-werner.com/" target="_blank">Tom Preston-Werner</a> en <a href="http://semver.org/" target="_blank">Semver.org</a> bajo licencia <a href="http://creativecommons.org/licenses/by/3.0/" target="_blank">Creative Commons 3.0</a>.