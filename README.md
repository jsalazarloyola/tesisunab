# tesisunab

Document class con formato de tesis siguiendo los requerimientos de la UNAB que funcione con pdflatex. 

Basado en el formato creado para la [USACH](https://github.com/jsalazarloyola/tesisusach/tree/master), por **Javier Salazar Loyola** (javier dot salazar dot l at usach dot cl).

## TODO:
* Documentar el código y sus funcionalidades.
* Documentar las opciones de la clase.
* Determinar si los entornos nuevos (teoremas) son necesarios o demasiado específicos.
* Chequeo de errores, opciones cruzadas o cosas así.

## Mini manual de uso:

El `ejemplo.tex` contiene una demostración de uso, con comentarios y sugerencias de creación del documento para tesistas (requiere paquete `lipsum`).

Para usar el formato, copiar los archivos `tesisunab.cls` e `images/LogoUNAB.png` en la carpeta del proyecto. Luego, iniciar con:

```\documentclass{tesisunab}```

Las opciones, hasta que logre documentarlas bien, son las mismas que las de la clase `book`, junto a unas extra, en la que se basa este formato. Ampliaré la documentación en el corto o mediano plazo.

### Algunas opciones de interés:

* `propuesta` Coloca, mediante el comando `\propuesta{param}`, el propósito o protocolo de titulación.
* `logo` Habilita el comando `\logo{param}` para incluir el logo desde otro lugar (por defecto, lo busca en `images/LogoUNAB.png`).
* `copyright` Coloca en la contracara de la página de título (i.e. página 2 del documento) el anuncio de copyright ingresado mediante el comando `\copyright{}`. El archivo `ejemplo.tex` contiene una demostración de este comando en funcionamiento.

### Consideraciones

* Los ambientes `resumenEs` y `resumenEn` crean *abstracts*, preparados para español e inglés, respectivamente (`resumenEn` se crea en un ambiente `otherlanguage` de Babel). Hasta ahora, tienen el bug de que *deben* definirse las palabras clave primero mediante `\keywordsEs{palabras}` y `\keywordsEn{words}`, respectivamente, ya que los *abstracts* ingresan las palabras como parte de su contenido.
* Se puede colocar una dedicatoria simple (una línea) mediante `\dedicatoriaSimple{dedicatoria}`. Una dedicatoria más larga, de una página o así, se puede crear con el ambiente `pagDedicatoria`
* La página de agradecimientos se puede generar con el ambiente `agradecimiento` y hace una función similar a la de dedicatoria.
* Abreviaturas de interés: `\ie` ("i.e."), `\eg` ("e.g.") y `\cf` ("cf.").

## Requerimientos y configuraciones básicas

La clase requiere paquetes básicos, pero entre otras cosas, carga `babel` configurado para idioma español, usar utf8 con `inputenc` y fuente T1. Además, carga el paquete `textcomp`, de modo que símbolos como `\textcopyright` están habilitados por defecto.

Además, utiliza `fancyhdr` para los encabezados, enumerate para listas (por lo que se puede configurar la numeración sin recurrir a otros paquetes, usando, por ejemplo, `\begin{enumerate}[i.]`), `graphicx`, `hyperref` y `multirow`.

Finalmente, debe decirse que la gestión bibliográfica se hace mediante BibLaTeX en formato APA, como piden varios departamentos de la universidad, por lo que usa el backend `biber` para generar las referencias.
