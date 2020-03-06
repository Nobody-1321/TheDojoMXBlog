---
title: "A Philosophy of Software Design: Ocultar información"
date: 2020-03-03
author: Héctor Patricio
tags: PoSD interfaces módulo complejidad diseño-de-software
comments: true
excerpt: "Ocultar información es una de las claves para reducir la complejidad, veamos algunas maneras de lograrlo."
header:
  overlay_image: https://res.cloudinary.com/hectorip/image/upload/c_scale,w_1800/v1583357998/IMG_3866_owfbzj.jpg
  teaser: https://res.cloudinary.com/hectorip/image/upload/c_scale,w_1800/v1583357998/IMG_3866_owfbzj.jpg
  overlay_filer: rgba(0, 0, 0, 0.5)
---

> La idea básica es que cada módulo debería encapsular algunas piezas de conocimiento, que representen decisiones de diseño. - **John Ousterhout**

En [el artículo anterior](https://blog.thedojo.mx/2020/03/02/a-philosophy-of-software-design-los-modulos-deben-ser-profundos.html) vimos por qué es bueno que los módulos sean profundos, es decir, oculten detalles de implementación y funcionalidades detrás de una interfaz lo más sencilla posible. En este y los siguientes artículos vamos a ver maneras prácticas de lograr esto, basado en ejemplos de ["A Philosophy of Software Design"](https://amzn.to/2H92nwA).

En este artículo hablaremos de cómo **ocultar información** que no es necesaria saber para usar los módulos, ya que complicaría su uso, creando [carga cognitiva](https://blog.thedojo.mx/2020/02/26/tres-formas-de-identificar-la-caomplejidad-posd6.html#carga-cognitiva), uno de los síntomas y consecuencias de la complejidad innecesaria.

Para saber cómo esconder la información debemos entender por dónde se escapa, prácticas comunes que llevan a un mal diseño y que pueden hacer que

## Fugas de información

Una fuga de información se entiende como revelar información que no deberíamos, porque se rompe el propósito del encapsulamiento en el módulo.

Recuerda la cita del principio: un módulo tiene que ocultar y mantener _decisiones de diseño_. Cuando esta decisión cambia y tienes que modificar varios módulos, tienes una fuga de información. En otras palabras, **una fuga de información sucede cuando una decisión de diseño se ve reflejada en varios módulos**.

Ejemplo. Piensa en una clase se conecte a una API para obtener información relacionada con los códigos postales. Para todos los usuarios de esta clase, debería ser **irrelevante** qué API se está usando, si es una API HTTP externa, un archivo gigantesco con todos los datos, una base de datos o lo que sea, mientras la clase cumpla con su trabajo.

Si al hacer cambios en esta decisión de diseño tienes que cambiar otras cosas a parte de esta clase, tienes algún tipo de fuga de información. ¿Ya pensaste en las formas en las que se puede escapar la información?

John Ousterhout sugiere hacerte la siguiente pregunta:

> ¿Cómo puedo reorganizar estas clases para que esta parte del conocimiento general sólo afecte a esta clase?

Hablemos de tres formas de crear fugas de información en nuestras clases, funciones o paquetes.

### Descomposición temporal

###