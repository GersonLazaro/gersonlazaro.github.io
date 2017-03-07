## gersonlazaro.com

Este es un blog creado utilizando el tema [Covalent](https://github.com/GersonLazaro/covalent) creado por Gerson Lázaro originalmente para [Ghost](https://www.ghost.org) y adaptado para utilizar en Jekyll utilizando el trabajo de [Jasper](https://github.com/biomadeira/jasper). 

## Live demo

[Gerson Lázaro](https://gersonlazaro.com)

## Instalación

Puede reutilizar este mecanismo para crear su propio blog a través de github. Sin embargo, tenga en cuenta que las siguientes instrucciones no están completas. De momento, este sitio ha sido realizado para uso personal y no como una plantilla, y si bien con los siguientes pasos tendrá su sitio funcionando, se recomienda enormemente que realice una revisión de los demás archivos del repositorio, especialmente de la carpeta _layouts, para remover cualquier rastro de información relacionada con este sitio (enlaces a suscripción, información del autor, redes sociales, entre otras):

1. Cree un fork de este repositorio.
2. Modifique la información del sitio, editando según sus datos las lineas 9 a la 22 del archivo _config.yml
3. Elimine el archivo CNAME
3. IMPORTANTE: Modifique la variable google_analytics de _config.yml (linea 23) por su propio código de seguimiento de Google Analytics, o elimine esta linea (Por favor, no olvide realizar este paso. Eso le permitirá realizar seguimiento de sus visitas, y evitará que sus datos afecten mi propio seguimiento).
4. IMPORTANTE: Modifique la variable disqus de _config.yml (linea 24) por su propio username de disqus para tener su propio sistema de comentarios (Por favor, no olvide realizar este paso para evitar que sus comentarios aparezcan en mi sitio y viceversa).
5. Elimine el contenido de la carpeta _posts, y añada en esta carpeta sus propias publicaciones. Antes de eliminarla, puede revisar alguna de las publicaciones para ver el formato de publicación. Son simples archivos markdown con algunas metatiquetas al inicio.
6. Haga clic en settings en el repositorio en Github, y asegurese de que la sección github pages esté correctamente inicializada (si desea que el blog tenga la dirección username.github.io, asegurese de colocar ese nombre al repositorio.

## Publicación

Basta con añadir archivos en formato markdown con los metadatos solicitados para que su sitio aparezca publicado.

