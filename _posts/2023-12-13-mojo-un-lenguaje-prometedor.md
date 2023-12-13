---
title: "Mojo 🔥: un lenguaje prometedor"
date: 2023-12-13
author: Héctor Patricio
tags: mojo python machine-learning
comments: true
excerpt: "El ecosistema de desarrollo está cambiando y se están diseñando nuevos lenguajes de programación y entornos de ejecución más adecuados para los problemas actuales. Hablemos de Mojo."
header:
  overlay_image: https://res.cloudinary.com/hectorip/image/upload/c_scale,w_1400/v1702275251/shubham-dhage-cLhjmsyby3Q-unsplash_ucy8y3.jpg
  teaser: https://res.cloudinary.com/hectorip/image/upload/c_scale,w_400/v1702275251/shubham-dhage-cLhjmsyby3Q-unsplash_ucy8y3.jpg
  overlay_filter: rgba(0, 0, 0, 0.5)
---

[Chris Lattner](https://www.nondot.org/sabre/){:target="_blank"}, uno de los creadores de [LLVM](https://llvm.org) y [Swift](https://www.swift.org/), ha estado desarrollando un nuevo lenguaje basado en la sintaxis de **Python** pero pensado para atacar su punto más débil: **la velocidad de ejecución**.

Este lenguaje se llama [Mojo](https://modular.com/mojo), y está siendo publicitado como un lenguaje para hacer aplicaciones de **inteligencia artificial**. Como ya dijimos, su enfoque principal está en ser un lenguaje que produzca programar eficientes, por lo que puede ser usado para cualquier aplicación que requiera alto rendimiento o hacer una gran cantidad de cálculos, justo como las aplicaciones de _machine learning_.

En este artículo veremos el motivo detrás de su nacimiento, sus características y analizaremos si te conviene aprenderlo o deberías buscar alguna otra alternativa. Primero, entendamos la fundación de Mojo.

## MLIR - Representación intermedia multi-capa

LLVM es un proyecto que se define como infraestructura para la construcción de compiladores. Imagínate que es como un framework para construir compiladores. Muchos de los lenguajes actuales están creados usando este proyecto. Por ejemplo [Rust](https://rust.org), Swift y [Julia](https://julialang.org) están construidos sobre LLVM.

Una de las partes que hace muy útil a LLVM es su **representación intermedia**. Esta representación intermedia permite que los diferentes lenguajes de programación que funcionan sobre él se aprovechen de las optimizaciones que LLVM hace sobre el código intermedio. El flujo del código es el siguiente:

1. El código fuente es compilado a código intermedio (**IR**).
2. El **IR** es optimizado.
3. El **IR** es compilado a código de máquina.

De hecho, se dice que Swift es sólo azúcar sintáctico sobre la representación intermedia de LLVM, es decir, que se parece mucho a esta representación intermedia y aprovecha sus características.

MLIR (Multi-layer Intermediate Representation o Representación intermedia multi-capa) es una representación intermedia de más alto nivel que la representación intermedia tradicional. No en el sentido de que sea más fácil de entender para los humanos, sino que en vez de mapearse directamente con una infraestructura de compilación, representa un modelo más abstracto que puede ser mapeado a diferentes infraestructuras de compilación, de manera especializada para cada una de ellas. Así permite que un mismo código fuente pueda ser compilado para diferentes ejecutores, como GPU's, TPU's, CPU's, etc, sin tener que crear una nueva representación intermedia o crear nuevo código fuente.

## Entra Mojo 🔥

Toda esta explicación anterior es para entender que Mojo es para MLIR lo que Swift es para LLVM. Aprovecha gran parte de las características de MLIR para crear un lenguaje de programación que pueda usar ejecutores especializados en cómputo de alto rendimiento como GPU's y TPU's, pero presentando una sintaxis más amigable para los humanos, a diferencia de CUDA, o C++, por ejemplo.

Mojo te ayuda aprovechar el paralelismo masivo de los GPU's sin tener que preocuparte por aprender un nuevo lenguaje o siquiera tener que pensar en dónde finalmente se ejecutará tu programa.

Ya que Python es la lingua franca del mundo de la inteligencia artificial, Mojo inicialmente fue pensado como una extensión de Python (lo que llamaríamos un superconjunto de Python), en el sentido de que todo el código válido en Python es código válido en Mojo, muy parecido a la relación que existe entre la sintaxis de TypeScript y JavaScript.

## Características de Mojo

Las pruebas iniciales de Mojo revelan que puede ser hasta **68,000** veces más rápido que Python en ciertas tareas (sí, leíste bien **sesenta y ocho mil**), mientras que C++ llega a ser **_sólo_ 5,000** veces más rápido. Claro, esto no habla muy bien de Python, pero debes pensar en que su objetivo no es ser un lenguaje de alto rendimiento, sino un lenguaje de alto nivel y fácil de usar.

Mojo quiere aprovechar la facilidad de uso de Python junto con su ecosistema de bibliotecas y desarrollos para hacer un ecosistema de desarrollo de inteligencia artificial más rápido y fácil de usar. Una de las primeras diferencias con Python es que es un lenguaje **compilado**.

Hablemos de algunas de las cosas que Mojo le aumenta a Python:

1. **Sistema de tipos progresivos**. Te permite usar el sistema de tipos tanto como lo necesites (por eso es progresivo). Pero debes tener en cuenta que los tipos te sirven tanto para verificar que el programa es correcto como **para optimizar el código que se genera**.

2. **Abstracciones sin costo**. Muy parecido a Rust, Mojo te da acceso a usar abstracciones de alto nivel que no incrementan el costo de ejecución.

3. **Seguridad de memoria**. Tiene un sistema de seguridad de memoria parecido al de Rust, mediante la pertenencia y el préstamo de referencias (ownership + borrow checker).

4. **Metaprogramación**. Te permite crear código parametrizado que se transforma en tiempo de compilación.

Como puedes ver, Mojo es un lenguaje muy interesante que aprovecha las características que hemos aprendido en lenguajes modernos que han sido útiles para crear mejores sistemas. El uso de MLIR es la base de su rendimiento, que permite que los programas que generas se puedan optimizar para ejecutores de diferentes tipos, incluidos algunos masivamente paralelos.

## ¿Deberías aprenderlo?

Mojo es un lenguaje que servirá tanto para hacer aplicaciones de IA como herramientas de bajo nivel para sistemas operativos, por lo que yo lo pensaría como un **lenguaje de programación de sistemas de última generación** que permitirá hacer cosas muy interesantes en el futuro.

Ahora mismo (Diciembre de 2023), es un lenguaje de código cerrado, es decir, su desarrollo está llevado por una empresa privada y el código fuente no está disponible para que otros lo vean o contribuyan. Según Lattner, esto permite inicialmente que se se avance de manera más efectiva, en lo que personalmente estoy de acuerdo. Se espera que Mojo sea de código abierto cuando alcance el nivel de madurez necesario.

Además, está en una etapa muy temprana de su desarrollo en la que ni siquiera cumple con todas las características de Python, por lo que todo lo que aprendas ahora sólo será un vistazo que te puede ayudar a definir si lo quieres usar cuando salga su versión lista para producción.

Personalmente, creo que es un buena inversión del tiempo si estás metido en crear aplicaciones de alto rendimiento, programación de sistema o quieres crear sistemas que usen inteligencia artificial como una de sus características principales. Por el contrario, para desarrollo web creo que tomará un poco más de tiempo en serte útil.

Otro caso para el que puede serte útil es para aprender las características de los lenguajes modernos, como los tipos progresivos o la seguridad de memoria mediante el préstamos de referencias.

## Conclusión

Mojo es un lenguaje interesante, muy prometedor y que está en la raya de la innovación en creación de lenguajes y características modernas. Si eres curioso y te gustan en general los lenguajes de programación, creo que es una gran opción para empezar a aprender y tal vez en el futuro recoger los beneficios si cumple con sus promesas.
