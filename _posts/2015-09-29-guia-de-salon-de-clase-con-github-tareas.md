---
layout: post
cover: 'content/images/2015/09/github_educacion_3-1.jpg'
title: 'Guía de salón de clase con Github: Tareas (II)'
date:   2015-09-29 06:07:00
categories: tech web
navigation: True
---
### Uso de repositorios

Primero, sigue las instrucciones para [configurar los repositorios de tareas][repository-setup]. Una vez creado, los repositorios deben ser inicializados con el contenido por defecto. Esto puede ser un simple archivo README, pero podría también incluir un archivo de código, función de inicialización, función main(), etc.

#### Páginas de proyecto

Si los estudiantes necesitan proporcionar materiales de apoyo, documentación, o entradas de blog acerca de su proyecto, puedes:

* Hacer commit con archivos [Markdown][markdown] directamente al repositorio
* Usar la [wiki del repositorio][wikis]
* Construir una página para el proyecto/clase en [Páginas Github][pages]

#### Testing automatizado

El [testing automatizado][automated-testing] (a menudo considerado como parte de la [integración continua][ci], or "CI") es una excelente manera de verificar rápidamente las soluciones de los estudiantes.  Su conjunto de pruebas podría incluir:

* Análisis estático
    * [Validación HTML][html-validator]
    * [JSHint][jshint]
    * [Cppcheck][cppcheck]
    * *y [muchas otras][static-analysis]*
* Pruebas unitarias
    * Las pruebas pueden ser escritas por ti o por los estudiantes
    * Ocultas para el estudiante o no

Hay muchas herramientas y servicios que pueden correr pruebas automatizadas, incluyendo:

* [Travis CI][travis]
* [Jenkins CI][jenkins]
* [Web-CAT][web-cat]
* [CodeClimate][code-climate]
* [Coveralls][coveralls]

Estas herramientas pueden ser configuradas para ejecutar las pruebas cada vez que un nuevo código es agregado por el estudiante al repositorio usando [webhooks][webhooks], aunque algunos realizan la configuración de forma automática.

### Recopilación de tareas

La mecánica recomendada para recoger las tareas depende de si se utiliza la estrategia de [fork][forks] or [sandbox][sandboxing].  En cualquier caso, la retroalimentación puede darse mediante pull request o [commits][commit-comments], o abriendo [issues][issues] en el repositorio de los estudiantes para que ellos lo "corrijan".  Esto puede ser hecho por los instructores, aunque es posible considerar la incorporación de revisión de código por pares como una manera de que los estudiantes practiquen el dar y recibir retroalimentación.  Tenga en cuenta que es posible que deba conceder a los estudiantes [acceso de solo lectura][access-permissions] a uno de los otros repositorios para permitir que vean los contenidos y dejen sus comentarios.

Una característica de Github que puede ser útil es utilizar los gráficos de [Red][network] y [contribuyentes][graphs], al igual que la lista de commits.  Como fue [señalado en la comunidad para docentes][community-graphs]:

> Tener los resúmenes analíticos de Github ha sido genial -- Solo tengo que revisar el gráfico de contribuyentes y rápidamente escanear los commits realizados.  Puedo ver quien hizo que, como y cuando en solo un par de segundos. También puedo ver el flujo de trabajo del proyecto.

Sin embargo, se advierte: no tomes los metadatos (o los gráficos generados por ellos) como un evangelio; un estudiante inteligente bien podría editar el(los) autor(es) del commit(s) o su fecha y hora después de los hechos.

<br><br>
###### Este post hace parte de la guía de salón de clase con Github
* Introducción: [Potenciando la educación con Github](https://gersonlazaro.com/potenciando-la-educacion-con-github/)
* Parte 1: [Guía de salón de clase con Github: Introducción](http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-introduccion)
* Parte 2: [Guía de salón de clase con Github: Tareas](http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-tareas)
* Parte 3: [Guía de salón de clase con Github: Configurando los repositorios](http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-configurando-los-repositorios)
* Parte 4: [Guía de salón de clase con Github: Forks (bifurcaciones)](http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-forks)
* Parte 5: [Guía de salón de clase con Github: Sandboxing](http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-sandboxing) 
* Parte 6: [Guía de salón de clase con Github: Repositorios Privados](http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-repositorios-privados) 


> Guía publicada originalmente en ingles en [Github for Education](https://education.github.com/guide) y compartida bajo licencia [Creative Commons 4.0](http://creativecommons.org/licenses/by/4.0/). Si considera que hay errores en la traducción puede colaborar [aquí](https://github.com/GersonLazaro/guide).

<!-- Links -->
[repository-setup]: http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-configurando-los-repositorios
[markdown]: https://guides.github.com/features/mastering-markdown/
[wikis]: https://guides.github.com/features/wikis/
[pages]: https://pages.github.com
[automated-testing]: https://en.wikipedia.org/wiki/Test_automation
[ci]: https://en.wikipedia.org/wiki/Continuous_integration
[html-validator]: http://validator.w3.org/source/
[jshint]: http://www.jshint.com/about/
[cppcheck]: http://cppcheck.sourceforge.net
[static-analysis]: https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis
[travis]: http://docs.travis-ci.com
[jenkins]: http://jenkins-ci.org
[web-cat]: http://web-cat.org
[code-climate]: https://codeclimate.com
[coveralls]: https://coveralls.io
[webhooks]: https://developer.github.com/webhooks/
[forks]: http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-forks
[sandboxing]: http://www.gersonlazaro.com/guia-de-salon-de-clase-con-github-sandboxing
[commit-comments]: https://help.github.com/articles/adding-commit-comments
[issues]: https://guides.github.com/features/issues/
[access-permissions]: https://help.github.com/articles/permission-levels-for-an-organization-repository
[network]: https://github.com/blog/39-say-hello-to-the-network-graph-visualizer
[graphs]: https://help.github.com/articles/using-graphs
[community-graphs]: https://github.com/education/teachers/issues/7
