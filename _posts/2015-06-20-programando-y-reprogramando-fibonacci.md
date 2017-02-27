---
layout: post
cover: 'content/images/2015/06/fibonacci.jpg'
title: Programando y reprogramando la sucesión de Fibonacci
date:   2015-06-20 06:06:00
categories: programacion
navigation: True
---

La conocida sucesión de Fibonacci es aquella sucesión que comienza con los términos 0 y 1, y continua obteniendo cada término sumando sus dos anteriores. Mas formalmente:
![Generalización de la sucesión de Fibonacci](/content/images/2015/06/generalizacion-fibonacci-1.png)

En este orden de ideas, es fácil descubrir los primeros términos de la sucesión: 0,1,1,2,3,5,8,13,21,34,55,89,144,... Del mismo modo podemos expresar cada termino en base a su función: **Fib(0)**=0, **Fib(1)**=1, **Fib(2)**=1, **Fib(3)**=2, **Fib(4)**=3, **Fib(5)**=5...

Dada esta definición formal, no es nada difícil crear una primera solución recursiva para obtener un término n de la sucesión de Fibonacci:
```
FUNCTION fibonacci(INTEGER n)
     IF (n<2) RETURN n
     ELSE
          RETURN fibonacci(n-1) + fibonacci(n-2)
```

Pero analicemos a fondo lo que hace esta función. Recursivamente, estará llamando a sus dos anteriores. Cada una de estas llamadas, si es mayor que 1, de nuevo estará llamando a sus dos anteriores. Analicemos el árbol de llamadas para un fibonacci de orden 6:
![Árbol fibonacci](/content/images/2015/06/arbol-fibonacci.png)

Este es un algoritmo de orden exponencial, mas exactamente ![phi^n](/content/images/2015/06/orden-fibonacci.png) La explicación de este costo puede ser algo extensa, así que si quieres leerla a fondo, te recomiendo leerla <a href="http://www.lcc.uma.es/~av/Libro/CAP1.pdf" target="_blank">aquí</a> (página 11). Esto significa que es terriblemente lento, pues tendrá que hacer excesivas operaciones para valores altos de n. 

###### ¿A que se debe esta ineficiencia?


Volvamos al árbol. Para calcular **1** vez Fib(6), es necesario calcular **1** vez Fib(5), **2** veces Fib(4), **3** veces Fib(3), **5** veces Fib(2), **8** veces Fib(1) y cinco veces Fib(0) (Como el algoritmo considera constante Fib(1), solo tenemos 5 llamadas a Fib(0). Si Fib(1) se calculara con su antecesor, tendríamos **13** llamadas). ¡Estamos repitiendo operaciones! Y lo peor, estas operaciones se repiten justamente siguiendo la secuencia de Fibonacci como se puede ver en los números en negrilla (1,1,2,3,5,8,13). 

###### ¿Como podemos mejorarlo?
Si eliminamos los cálculos repetidos, fácilmente podemos tener un algoritmo de **O(n)**. Para hacer esto, utilizaremos un array que guarde los valores calculados para hallar el siguiente valor:

```
FUNCTION fibonacci(ARRAY[n+1] terminos, INTEGER n)
     IF(n<2)
          RETURN n
     ELSE
          terminos[0]=0
          terminos[1]=1 
          FOR(INTEGER i IN RANGE [2,n])
                terminos[i] = terminos[i-1] + terminos[i-2]
          RETURN T[n]
```

Ahora el algoritmo es mucho mas eficiente, reduciendo enormemente el número de operaciones innecesarias para valores altos de n. Pero surge un nuevo problema. La complejidad espacial es de **O(n)** también. Hemos sacrificado espacio por tiempo, ahora tenemos un array de n posiciones cuando en realidad solo necesitábamos la posición n y las demás podemos desecharlas. 

Como el algoritmo ÚNICAMENTE necesita de los dos valores anteriores para obtener el siguiente, podemos evitar el array, y así reducir su espacio ocupado:


###### Reduciendo costo espacial
```
FUNCTION fibonacci(INTEGER n)
    INTEGER a = 0, b = 1, c
    FOR(INTEGER i = 0; i < n; i++)
        c = a + b
        a = b
        b = c    
    RETURN a
```

Ahora la complejidad temporal sigue siendo de orden **O(n)** pero la complejidad espacial se reduce a un orden **O(1)**

###### ¿Que tal un algoritmo O(log<sub>2</sub>n)?
Volviendo al inicio, sabemos que:
![Fib(n)=Fib(n-1)+Fin(n-2)](/content/images/2015/06/fibonacci-formula-gen.png)

Partiendo de aquí, podemos fácilmente desarrollar un sistema de ecuaciones:
![Ecuaciones](/content/images/2015/06/matriz1.png)
Y por supuesto, lo reescribiremos en notación matricial:
![Matriz Fibonacci](/content/images/2015/06/matriz2.png)
Verificando estos valores para n = 2
![](/content/images/2015/06/matriz-fibonacci-n-1.png)
Conociendo que **Fib(0)**=0 y **Fib(1)=1**:
![](/content/images/2015/06/matriz-1-1.png)
Y efectivamente, **Fib(2)**=1. Ahora bien, generalizando para diferentes valores de n.
![](/content/images/2015/06/ec4.png)
![](/content/images/2015/06/ec5.png)

Ahora recordemos 3 propiedades de la potenciación:
![](/content/images/2015/06/leyes-1.png)
Los cuales nos permitirán hacer un "divide y vencerás" para resolver la potencia de una manera eficiente:
![](/content/images/2015/06/potencias.png)
Ahora si, procedemos al algoritmo:
```
FUNCTION fibonacci(INTEGER n)
     INTEGER h,i,j,k,aux
     h = i = 1
     j = k = 0
     WHILE (n > 0)
         IF ( n % 2 != 0)
             aux = h*j
             j = h*i + j*k + aux
             i = i*k + aux
         aux = h*h
         h = 2*h*k + aux
         k = k*k + aux
         n = n/2
     RETURN j
```
¿Que demonios he hecho? Básicamente, partir el problema. Para explicarlo, miremos paso a paso el proceso para hallar el **Fib(11)**:
![](/content/images/2015/06/sola.png)
![](/content/images/2015/06/solucion2.png)
Y así llegamos a la respuesta de manera mas rápida, en un orden O(log<sub>2</sub>n). Para hacernos una idea, para calcular el Fib(200) con el algoritmo exponencial, ocuparíamos 6.2737x10^41 cálculos (interminable). Con el algoritmo de orden n ocuparíamos 200 cálculos, y con este algoritmo, 8 operaciones (Por supuesto estos datos son aproximados, pero muestran claramente las diferencias abismales)  
###### Una última mejora

Ok ok, esto no es una última mejora, en realidad es un cambio total. Hasta ahora hemos manejado cada término de la sucesión en base a sus términos anteriores. Pero existe también una formula explicita creada por Lucas para hallar directamente un término sin necesidad de iterar.
![Formula explicita de fibonacci](/content/images/2015/06/formula-explicita-fibonacci.png)

Partiendo de esta formula, podemos crear esta función:

```
FUNCTION fibonacci(int n)
    DOUBLE raiz = sqrt(5)
    DOUBLE rta = ((1/raiz)*(pow((1+raiz)/2,n)) - (1/raiz)*(pow((1-raiz)/2,n)))
    RETURN rta
```


Esta función es muy eficiente, pero su orden depende de la manera de implementar la potenciación. Una potenciación por cuadrados como en el caso anterior, arroja un costo de O(log<sub>2</sub>n). Pero se debe tener mucho cuidado en su implementación, pues cada lenguaje tiene diferentes maneras de implementar las funciones matemáticas, y muy posiblemente sea necesario redondear el número para dar la respuesta exacta.


###### Algunas generalidades

* En muchos sitios, incluso textos es común leer "serie Fibonacci". Esto es un error, fibonacci es una sucesión, no una serie. Una sucesión es un conjunto de elementos con cierto orden, la serie por su parte es la suma de los términos de una sucesión.

* La sucesión de Fibonacci crece rápidamente, así que si van a calcularse valores muy altos, deben tomarse las medidas necesarias para evitar que exceda el tamaño del tipo de datos indicado.

* El verdadero nombre del ideador de la sucesión es Leonardo de Pisa, no Fibonacci. Este sobrenombre viene de su padre quien era apodado "Bonacci" (Bien intencionado), y se convierte en Filius Bonacci (Hijo de Bonacci) que termina siendo reducido a Fibonacci.

> Si encuentran algún error en esta publicación (lo cual es muy posible dado la cantidad de números, matrices y códigos que contiene) pueden reportarlo <a href="mailto:gersonlazaro@gersonlazaro.com">aqui</a>. Muchas gracias.