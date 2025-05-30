---
title: "¿Qué es la búsqueda binaria?"
date: 2024-10-26
author: Héctor Patricio
tags: algoritmos búsqueda
comments: true
excerpt: "Hablemos de un algoritmo sencillo que incluso utilizamos en la vida real pero que es
muy importante en el mundo de la computación."
usemathjax: true
header:
  overlay_image: https://res.cloudinary.com/hectorip/image/upload/c_scale,w_1400/v1729489258/nastya-kvokka-Ifk3WssHNRw-unsplash_m2u7vh.jpg
  teaser: https://res.cloudinary.com/hectorip/image/upload/c_scale,w_400/v1729489258/nastya-kvokka-Ifk3WssHNRw-unsplash_m2u7vh.jpg
  overlay_filter: rgba(0, 0, 0, 0.5)
---

Uno de los algoritmos más fáciles de entender, que incluso sin preparación
aplicamos en la vida real y que se enseña en las primeras clases de programación
es la **búsqueda binaria**. Vamos a hablar de este algoritmo y su relación
profunda con las ciencias de la computación y la información en general.

## Búsqueda binaria en la vida real

¿Alguna ves has jugado "Adivina Quién"? Es un juego de mesa en el
que cada jugador tiene un tablero con un conjunto de personajes con
características físicas distintas, como el color de pelo, diferentes
accesorios, y otros rasgos distintivos. Cada jugador escoge secretamente
un personaje y el otro lo tiene que adivinar, haciendo preguntas que
le permitan ir eliminando a los personajes que el otro jugador no ha elegido.
¿Cuál es la mejor estrategia para adivinar con la menor cantidad de
preguntas? Podrías pensar que es por cosas muy distintivas, por ejemplo,
si hay dos personajes con sombrero, y preguntas si tiene sombrero, puede
parecer una buena estrategia, pero no lo es.

En este caso, suponiendo que tenemos 40 personajes y solo dos tienen sombrero y
suponiendo que tienes 40 personajes, sólo 5% de las veces te ayudará reducir
significativamente el número de personajes, por lo que la mayoría de las veces
será una pregunta extra si la haces inicialmente. Lo mejor es empezar por las
características que dividan el conjunto de personajes en dos grupos más o menos
iguales. Por ejemplo, si hay 40 personajes y 20 tienen el pelo largo y 20 el corto,
la pregunta si el personaje tiene el pelo largo, te dejará con 20 personajes.
La siguiente pregunta debería ser algo similar.

Esto es exactamente lo que hace la búsqueda binaria, ir partiendo el conjunto
de elementos en dos grupos más o menos iguales e ir eliminando la mitad en cada
paso.

## Búsqueda binaria en la computación

El algoritmo de búsqueda binaria se aplica para encontrar un valor en una
colección _ordenada_ de elementos. Esto es para tener una forma sencilla de
eliminar la mitad del espacio de búsqueda en cada paso. Y puedes pensar justamente
que la necesidad de tener que ordenar los elementos es precisamente una de sus
des

## Implementación en pseudocódigo

Aquí puedes ver una implementación de la búsqueda binaria en pseudocódigo:

```
búsqueda_binaria(arreglo, elemento_buscado):
    inicio = 0
    fin = longitud(arreglo) - 1
    mientras inicio <= fin:
        medio = (inicio + fin) // 2  # división entera

        si arreglo[medio] == elemento_buscado:
            retornar medio
        sino si arreglo[medio] < elemento_buscado:
            inicio = medio + 1
        sino:
            fin = medio - 1
    retornar -1  # Elemento no encontrado
```

En pocas palabras, nombramos dos índices, `inicio` y `fin`, que van a ser
los que nos dicen en qué parte vamos a buscar. Después, calculamos el centro
de la lista, sumando el inicio y el fin y dividiendo entre dos. Otra forma de
calcularlo sería restando el inicio y el fin, dividiendo entre dos y sumándole
el inicio. Estas dos formas son equivalentes.

Ahora, comparamos el elemento buscado con el elemento en el centro. Si es igual,
hemos encontrado el elemento y terminamos. Si es menor, tenemos que agarrar 
la parte de la lista que está a la derecha, es decir, los elementos mayores.
Para esto, el inicio es un elemento a la derecha del medio (`inicio = medio + 1`)
y el fin se queda igual. Si el elemento buscado es mayor, tenemos que agarrar
la parte de lista que está a la izquierda, y ahora el que cambia es el fin.

De esta manera, en cada paso nuestro espacio de búsqueda se reduce a la mitad.

Si llegamos a un punto en el que el inicio es mayor que el fin, entonces no
encontramos el elemento y retornamos -1 (el -1 es una forma de que el
programa nos diga que no encontramos el elemento, muy usada en programación).

## Complejidad

Con un arreglo pequeño pensarás que la búsqueda binaria es más lenta una búsqueda
aleatoria o secuencial y así es, pero recuerda que los algoritmos eficientes
se notan cuando el tamaño de los datos crece.

Al ir cortando sucesivamente a la mitad el espacio de búsqueda, la complejidad
de la búsqueda binaria crece en forma logarítmica.

Expliquemos un poco eso. Un logaritmo es la función que nos ayuda a encontrar
el exponente al que hay que elevar un número para obtener otro. En la búsqueda
binaria, el número que queremos "obtener" (en verdad, es recorrer) es el número
de elementos en el arreglo que vamos a buscar.

Suponiendo que en cada paso hacemos más o menos 5 operaciones, por ejemplo,
para buscar en un arreglo de 1000 elementos y tomando en cuenta lo que hemos
visto de cómo se va reduciendo el espacio de búsqueda, tendríamos la siguiente
sucesión:

Elementos por buscar: 1000

Operaciones totales: 5

---

Elementos por buscar: 500

Operaciones totales: 10

---

Elementos por buscar: 250

Operaciones totales: 15

---

Elementos por buscar: 125

Operaciones totales: 20

---

Elementos por buscar: 62

Operaciones totales: 25

---

Elementos por buscar: 31

Operaciones totales: 30

---

Elementos por buscar: 15

Operaciones totales: 35

---

Elementos por buscar: 7

Operaciones totales: 40

---

Elementos por buscar: 3

Operaciones totales: 45

---

Elementos por buscar: 1

Operaciones totales: 50

---

Observa cómo es que el número de operaciones no creció al mismo ritmo que el número de
elementos. El número de operaciones creció sumó sólo 5 operaciones cada que duplicamos
el número de elementos. Aquí es donde está el logaritmo, como estamos duplicando o
multiplicando por dos, la base de nuestro logaritmo es el 2. ¿Cuánto "pasos" vamos a
tener que hacer? Cuantas veces tengamos que duplicar el número de elementos para llegar
al número total de elementos del arreglo en el peor de los casos. Esto es el logaritmo
base 2.

Así que la complejidad de la búsqueda binaria es $$O(\log n)$$. Donde $$n$$ es el
número de elementos en el arreglo.

## Implementaciones

Vamos a ver dos implementaciones en Python, una iterativa y otra recursiva.

Empezamos con la iterativa:

```python
def binary_search(arreglo, elemento_buscado):
    inicio = 0
    fin = len(arreglo) - 1
    while inicio <= fin:
        medio = (inicio + fin) // 2
        if arreglo[medio] == elemento_buscado:
            return medio
        elif arreglo[medio] < elemento_buscado:
            inicio = medio + 1
        else:
            fin = medio - 1
    return -1

```

Y la versión recursiva:

```python

def binary_search(arreglo, elemento_buscado, inicio=0, fin=None):
    if fin is None:
        fin = len(arreglo) - 1
    if inicio > fin:
        return -1
    medio = (inicio + fin) // 2
    if arreglo[medio] == elemento_buscado:
        return medio
    elif arreglo[medio] < elemento_buscado:
        return binary_search(arreglo, elemento_buscado, medio + 1, fin)
    else:
        return binary_search(arreglo, elemento_buscado, inicio, medio - 1)
```

Debido a la sintaxis de Python, la versión recursiva es un poco más verbosa,
por el manejo que tienes que hacer de los parámetros por defecto, pero si no
fuera por eso, en general me gusta más la versión recursiva.

Finalmente, si quieres hacer un programa que funcione con esta forma de búsqueda,
tienes que asegurarte de que las inserciones en el arreglo sean ordenadas, una forma
sencilla es usar un algoritmo parecido para encontrar el lugar adecuado para insertarlo.

## Uso en el mundo real

Lo que vimos en la sección anterior es para que entiendas cómo funciona, pero
lenguajes como Python, Ruby y otros, probablemente ya tengan implementaciones de
este algoritmo muy común. Por ejemplo, en Python tenemos el módulo `bisect` que 
permite hacer lo mismo con muchas menos líneas. Ejemplo:

```python
import bisect

lista = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
elemento = 5

indice = bisect.bisect_left(lista, elemento) # en realidad nos dice el valor más pequeño que es mayor o igual al elemento buscado

# si el índice es más grande que el número de elementos, no está en la lista
if indice != len(lista) and lista[indice] == elemento: 
    print(f"El elemento {elemento} está en el índice {indice}")
else:
    print(f"El elemento {elemento} no está en la lista")
```

Puedes ver más detalles del módulo `bisect` en la [documentación oficial](https://docs.python.org/3/library/bisect.html).

## Conclusión

La búsqueda binaria es uno de los algoritmos que todos los desarrolladores deberíamos conocer.
Espero que este artículo te haya ayudado a entender cómo funciona y su importancia.