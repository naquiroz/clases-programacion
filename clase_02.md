---
theme: apple-basic
info: |
  ## Primer clase de clases particulares de programación
drawings:
  persist: false
transition: slide-left
title: Clases particulares de programación
fonts:
  # basically the text
  sans: 'Inter,Noto Color Emoji'
  # use with `font-serif` css class from windicss
  serif: 'Inter,Noto Color Emoji'
  # for code blocks, inline code, etc.
  mono: 'Hack,Noto Color Emoji'
  weights: '300,700,900'
layout: intro
level: 1
hideInToc: true
download: true
presenter: dev
exportFilename: clase_01

addons:
  - slidev-addon-python-runner

# Optional configuration for this runner
python:
  # Install packages from PyPI. Default: []
  installs: ["cowsay"]

  # Automatically load the imported builtin packages. Default: true
  loadPackagesFromImports: true

  # Disable annoying warning from `pandas`. Default: true
  suppressDeprecationWarnings: true

  # Always reload the Python environment when the code changes. Default: false
  alwaysReload: true

  # Options passed to `loadPyodide`. Default: {}
  loadPyodideOptions: {}
---

# Bienvenidos/as a Xcode Academy

## Introducción a la programación
### Nicolás Quiroz

---
layout: center
level: 1
title: Agenda
hideInToc: true
---

# Agenda

<Toc maxDepth=1 />

---
layout: two-cols
level: 1
title: Motivación - blockly
hideInToc: false
---

# Motivación
## Recordando ejercicios blockly

Recuerdan el ejercicio de la clase 01 de blockly?

❗ Primero el "jugador" observaba que tenía en su costado izquierdo. Luego, dependiendo de lo que tenía, hacía una acción.

❗Si lo escribiéramos en ingles sería algo así:

```text
IF there is a path to the left
  girar a la izquierda
ELSE
  no hacer nada
```

Notamos que no es necesario escribir el `ELSE`, ya que si no hay un camino a la izquierda, no hacemos nada.

::right::

<img class="rounded-xl" src="/content/clase_02/blockly_if.png" alt="blockly if else" width="400"/>

---
layout: section
level: 1
title: If - introducción
hideInToc: false
---

# If
## Introducción

---
layout: two-cols
level: 2
title: If - sintaxis
hideInToc: false
---

# If/else

Sintaxis en Python:

```python {2-3} {lines:true}
... # Algoritmo antes
if CONDICION:
    instruccion
... # Algoritmo después
```

- Si la condición es `True`, se ejecuta el **código indentado**.
- Es super importante la indentación, ya que es lo que le dice a Python que se ejecute `instruccion` si la condición es `True`.
- Si hubiera más instrucciones indentadas, se ejecutarían todas única y exclusivamente si la condición es `True`.

::right::

```mermaid {theme: 'neutral', scale: 0.8, flowchart: { curve: 'stepAfter' }}
flowchart TD
    A[Algoritmo antes] --> B{CONDICION}
    B --- |True| C[instruccion]
    C --- D[ ]
    B --- |FALSE| D
    D --- E[Algoritmo después]
    style D width:0;
```

---
layout: full
level: 2
title: If - condiciones
hideInToc: false
---

# If
## ¿Qué es una `condición`?

💡 Es cualquier expresión que se pueda evaluar como `True` o `False` (es cualquier expresión que entregue un valor booleano).

❓ ¿Se les ocurren ejemplos?

<v-clicks>

- Que el usuario haya ingresado un número par.
- Que el usuario haya ingresado un número impar.
- Que el usuario haya ingresado un número mayor que 10.
- Que el texto ingresado por el usuario sea "hola".
- Que el resultado de sumar dos números sea mayor que un numero
- Que el resultado de unir strings sea igual a otro string
</v-clicks>

---
layout: default
level: 2
title: If - condiciones tabla
hideInToc: true
---

**Recordar** que en la [clase 01](/clase_01) vimos los operadores de comparación, todos ellos entregan un valor booleano. Más adelante veremos otras "_cosas_" que también entregan un valor booleano.

| Operación | Descripción | Ejemplo | Resultado |
| --------- | ----------- | ------- | --------- |
| `==` | Igual | `1 == 2` o `"hola" == "chao"` | `False` |
| `!=` | Distinto | `1 != 2` o `"dormir" != "siesta"` | `True` |
| `<` | Menor que | `1 < 2` | `True` |
| `>` | Mayor que | `1 > 2` | `False` |
| `>=` | Mayor o igual que | `1 >= 2` | `False` |
| `<=` | Menor o igual que | `1 <= 2` | `True` |

💡 Ahora que sabemos lo que son las **variables**, también podemos usarlas en las comparaciones.

---
layout: default
level: 2
title: If - condiciones - ejemplos
hideInToc: true
---

# If
## Ejemplos

Un programa que diga "NECESITO CAFEEEEE" solamente si el usuario ingresa un nivel de energía menor a 10, pueden asumir que el usuario siempre ingresa un número decimal (float), y luego diga "Hasta luigi. Fin del algoritmo"

```python
nivel_energia = float(input())
if nivel_energia < 10:
    print("NECESITO CAFEEEEE")
print("Hasta luigi. Fin del algoritmo")
```

---
layout: default
level: 2
title: If - condiciones - ejemplos
hideInToc: true
---

# If
## Ejemplos

Un programa super seguro que, pida una contraseña para ingresar al sistema. Si la contraseña es "mi_password" entonces imprime "Bienvenido al sistema", y luego diga "Disfurta!". Luego, aún cuando la contraseña sea incorrecta, diga "Fin del algoritmo".

```python
password = input()
if password == "mi_password":
    print("Bienvenido al sistema")
    print("Disfurta!")
print("Fin del algoritmo")
```

---
layout: center
level: 1
title: Y si quiero hacer algo si la condición es `False`?
hideInToc: true
---

# Y el "sino"?
## Si quiero hacer algo si la condición es `False`

---
layout: two-cols
level: 1
title: If/else - introducción
hideInToc: false
---

# If/else
## Introducción

❓¿Qué ocurre si ahora quiero hacer algo solamente cuando la condición no se cumple?

```python {2-5} {lines:true}
... # Algoritmo antes
if CONDICION:
    instruccion
else:
    otra_instruccion
... # Algoritmo después
```

- Si la condición es `True` (se cumple), se ejecuta la `instruccion` indentada.
- Si la condición es `False`, solamente se ejecuta la `otra_instruccion` indentada.
- En ambos casos, se ejecuta el "Algoritmo después".

::right::

```mermaid {theme: 'neutral', scale: 0.8, flowchart: { curve: 'stepAfter' }}
flowchart TD
    A[Algoritmo antes] --> B{CONDICION}
    B -->|True| C[instruccion]
    C --- D[ ]
    B --- |FALSE| F[otra_instruccion]
    F --- D
    D --- E[Algoritmo después]
    style D width:0;
```

---
layout: default
level: 2
title: If/else - ejemplos
hideInToc: true
---

# If/else
## Ejemplos

Un programa que diga "NECESITO CAFEEEEE" solamente si el usuario ingresa un nivel de energía menor a 10. Si el nivel de energía es mayor o igual a 10 "Estoy bien, puedo seguir", entonces diga "Hasta luigi. Fin del algoritmo"

```python
nivel_energia = float(input())
if nivel_energia < 10:
    print("NECESITO CAFEEEEE")
else:
    print("Estoy bien, puedo seguir")
print("Hasta luigi. Fin del algoritmo")
```

---
layout: default
level: 2
title: If/else - ejemplos
hideInToc: true
---

# If/else
## Ejemplos

Un programa que diga clasifique un restaurant con "Bueno/Malo" según el puntaje (de 0 a 100).
Si es menos que 30 es "Malo", si es mayor o igual que 30 es "Bueno".

```python
puntaje = int(input())
if puntaje >= 30:
    print("Bueno")
else:
    print("Malo")
```

❓ Y si quiero que sea "Bueno" si es mayor o igual que 60, "Regular" si es
mayor o igual que 30 y menor que 60, y "Malo" si es menor que 30?

```python
puntaje = int(input())
if puntaje >= 60:
    print("Bueno")
else:
    if puntaje >= 30:
        print("Regular")
    else:
        print("Malo")
```

❓ No hay una forma más fácil de hacerlo?

---
layout: section
level: 1
title: If/elif/else
hideInToc: false
---

# If/elif/else

---
layout: two-cols
level: 2
title: If/elif/else - introducción
hideInToc: true
---

# If/elif/else
## Introducción

```python {2-3|4-5|6|7-8|9-10|2-10} {lines:true}
... # Algoritmo antes
if CONDICION_1:
    instruccion_1
elif CONDICION_2:
    instruccion_2
... # Varios elif
elif CONDICION_N:
    instruccion_N
else:
    otra_instruccion
... # Algoritmo después
```

::right::

- Si la `CONDICION_1` es `True`, se ejecuta la `instruccion_1` indentada.
- Si la `CONDICION_1` es `False`, se evalúa la `CONDICION_2`.
- Si la `CONDICION_2` es `True`, se ejecuta la `instruccion_2` indentada.
- Si la `CONDICION_2` es `False`, se evalúa la `CONDICION_3` y así sucesivamente.
- Si ninguna de las condiciones es `True`, se ejecuta la `otra_instruccion` indentada.
- En todos los casos, se ejecuta el "Algoritmo después".

❗ **IMPORTANTE**: Si una condición es `True`, no se evalúan las siguientes condiciones, ni siquiera si son `True`.

---
layout: center
level: 2
title: If/elif/else - diagrama
hideInToc: true
---

# If/elif/else
## Diagrama

```mermaid {theme: 'neutral', scale: 0.8, flowchart: { curve: 'stepAfter' }}
flowchart LR
    A[Algoritmo antes] --> B{CONDICION_1}
    B --- |True| C[instruccion]
    C --- D[ ]
    B --- |FALSE| F{CONDICION_2}
    G --- D
    F --- |False| D
    F --- |True| G[instruccion_2]
    D --- E[Algoritmo después]
    style D width:0;
```

Y así sucesivamente para cada `elif` y `else` al final.
---
layout: default
level: 2
title: If/elif/else - ejemplos
hideInToc: true
---

Usando el ejemplo anterior, ahora queremos que sea "Bueno" si es mayor o igual que 60, "Regular" si es mayor o igual que 30 y menor que 60, y "Malo" si es menor que 30.

```python {1-7} {lines:true}
puntaje = int(input())
if puntaje >= 60:
    print("Bueno")
elif puntaje >= 30:
    print("Regular")
else:
    print("Malo")
```

Y si le agregamos un `elif` más?

```python {1-9} {lines:true}
puntaje = int(input())
if puntaje >= 90:
    print("Excelente")
elif puntaje >= 60:
    print("Bueno")
elif puntaje >= 30:
    print("Regular")
else:
    print("Malo")
```

---
layout: two-cols
level: 2
title: Ejemplo avanzado
hideInToc: false
---

# Ejemplo avanzado

Eres un programador de **Xpendit**, una plataforma de rendición de gastos empresariales. Tu tarea es implementar la lógica que determina a qué **flujo de aprobación** debe enviarse cada gasto, según ciertas reglas de negocio.

En Xpendit existen **tres flujos de aprobación**:

1. **Flujo "Directo Gerencia"**:
   - Centro de costos: "Marketing"
   - Categoría: "Publicidad"
   - Monto: mayor o igual a $1.000.000
   - Persona que rinde: cualquier persona

::right::

2. **Flujo "Aprobación Finanzas"**:
   - Centro de costos: "Operaciones"
   - Monto: menor a $500.000
   - Persona que rinde: "Juan Pérez" o "María López"

3. **Flujo "Aprobación Jefatura"**:
   - Categoría: "Viajes"

Tu programa debe pedir los datos de **dos gastos distintos** (centro de costos, categoría, monto y persona que lo rinde) y, para cada uno, imprimir el nombre del flujo de aprobación que le corresponde. Puedes asumir que siempre alguno de los tres flujos aplica.

---
layout: two-cols
level: 2
title: Ejemplo de entrada y salida
hideInToc: true
---

### Ejemplo de entrada y salida

```text
Centro de costos: Marketing
Categoría: Publicidad
Monto: 1500000
Persona que rinde: Ana Torres

Centro de costos: Operaciones
Categoría: Insumos
Monto: 300000
Persona que rinde: Juan Pérez
```

```text
El flujo para el primer gasto es: Directo Gerencia
El flujo para el segundo gasto es: Aprobación Finanzas
```

::right::

Otro ejemplo:

```text
Centro de costos: Ventas
Categoría: Viajes
Monto: 200000
Persona que rinde: María López

Centro de costos: Marketing
Categoría: Viajes
Monto: 800000
Persona que rinde: Pedro Soto
```

```text
El flujo para el primer gasto es: Aprobación Jefatura
El flujo para el segundo gasto es: Aprobación Jefatura
```

---
layout: default
level: 2
title: Solución
hideInToc: false
---

# Solución

```python {1-15|16-30}{lines:true, maxHeight: '300px'}
# Primer gasto
print("Ingrese los datos del primer gasto:")
centro_costos1 = input("Centro de costos: ")
categoria1 = input("Categoría: ")
monto1 = int(input("Monto: "))
persona1 = input("Persona que rinde: ")


# Segundo gasto
print("Ingrese los datos del segundo gasto:")
centro_costos2 = input("Centro de costos: ")
categoria2 = input("Categoría: ")
monto2 = int(input("Monto: "))
persona2 = input("Persona que rinde: ")

if centro_costos1 == "Marketing" and categoria1 == "Publicidad" and monto1 >= 1000000:
    print("El flujo para el primer gasto es: Directo Gerencia")
elif centro_costos1 == "Operaciones" and monto1 < 500000 and (persona1 == "Juan Pérez" or persona1 == "María López"):
    print("El flujo para el primer gasto es: Aprobación Finanzas")
elif categoria1 == "Viajes":
    print("El flujo para el primer gasto es: Aprobación Jefatura")


if centro_costos2 == "Marketing" and categoria2 == "Publicidad" and monto2 >= 1000000:
    print("El flujo para el segundo gasto es: Directo Gerencia")
elif centro_costos2 == "Operaciones" and monto2 < 500000 and (persona2 == "Juan Pérez" or persona2 == "María López"):
    print("El flujo para el segundo gasto es: Aprobación Finanzas")
elif categoria2 == "Viajes":
    print("El flujo para el segundo gasto es: Aprobación Jefatura")
```

---
layout: center
level: 1
title: Spoiler while
hideInToc: true
---

# Coming soon...

En el último ejemplo,  preguntamos dos veces por el monto de los gastos, y luego preguntamos por la persona que rinde. Qué pasa si queremos preguntar estas cosas una sola vez?

Para eso sirve el `while`, que comenzaremos a ver en la próxima clase.

---
layout: default
level: 1
title: Ejemplo - Pre ciclos
hideInToc: false
---

# Ejemplo

Haz un algoritmo que le pida al usuario un número (mayor a 0), y luego imprima todos los números desde el 1 hasta el número ingresado por el usuario.

Por ejemplo si el usuario ingresa 4, el programa debe imprimir:

```text
1
2
3
4
```

```python
numero = int(input())
if numero >= 1:
    print(1)
if numero >= 2:
    print(2)
if numero >= 3:
    print(3)
if numero >= 4:
    print(4)
```

❓ Y si el usuario ingresa 5? O 100? O 1000000?

---
layout: two-cols
level: 2
title: Usar while en vez de if
hideInToc: true
---

# Motivación

Cuando las condiciones son muchas, es muy tedioso escribir un `if` por cada una de ellas.
No podemos ponernos en todos los casos específicos, pero podemos hacer algo más general.

1. Podemos buscar un patrón en las condiciones.
2. Con el patrón, podemos escribir un algoritmo que se repita.
3. Podemos encontrar la condición de término del algoritmo y con eso, escribir un código que se repita hasta que se cumpla la condición de término.

::right::

<div class="mt-25 h-100 flex flex-col justify-around">
    <img class="rounded-xl" src="/content/clase_02/meme_ifs.jpg" alt="blockly for"/>
</div>

---
layout: two-cols
level: 1
title: Motivación - blockly
hideInToc: false
---

# Motivación
## Recordando ejercicios blockly (nuevamente)

Recuerdan el ejercicio de la clase 01 de blockly?

❗ En el primer caso, el jugador avanzaba una cantidad específica de pasos, y en el segundo caso, avanzaba hasta que se cumpliera una condición.

❗Si lo escribiéramos en ingles sería algo así:

```text
FOR 3 times
    avanzar
    avanzar
    girar_derecha
```

O bien

```text
WHILE no piggie
  avanzar
```

Cuando queremos repetir algo una cantidad específica de veces, usamos el `for`, y cuando queremos repetir algo hasta que se cumpla una condición, usamos el `while`.

::right::

<div class="mt-25 h-100 flex flex-col justify-around">
    <img class="rounded-xl w-1/2" src="/content/clase_02/blockly_for.png" alt="blockly for"/>
    <img class="rounded-xl w-1/2" src="/content/clase_02/blockly_while.png" alt="blockly while"/>
</div>

---
layout: section
level: 1
title: While - introducción
hideInToc: false
---

# While
## Repetir algo hasta que se cumpla una condición

---
layout: two-cols
level: 2
title: While - sintaxis
hideInToc: false
---

# While

Sintaxis en Python:

```python {2-3} {lines:true}
... # Algoritmo antes
while CONDICION:
    instruccion
... # Algoritmo después
```

- Si la condición es `True`, se ejecuta el **código indentado**. Este código se repite **hasta que la condición sea `False`**.
- Al igual que en el `if/else` es muy importante la indentación.

::right::

```mermaid {theme: 'neutral', scale: 1.2, flowchart: { curve: 'stepAfter' }}
flowchart TD
    A[Algoritmo antes] --> B{CONDICION}
    B --> |True| C[instruccion]
    C --> B
    B --> |FALSE| E[Algoritmo después]
```

---
layout: full
level: 2
title: While - condiciones
hideInToc: false
---

# While
## ¿Qué es una `condición`?

💡 Al igual que en los `if` es cualquier expresión que se pueda evaluar como `True` o `False` (es cualquier expresión que entregue un valor booleano).

❓ ¿Se les ocurren ejemplos para el while?

<v-clicks>

- Hasta que el usuario ingrese un número mayor que 10.
- Hasta que el usuario haya ingresado un número par.
- Hasta que el texto ingresado por el usuario sea el valor esperado.
- Hasta que el resultado de sumar dos números sea mayor que un numero
- Hasta que el resultado de unir strings sea igual a otro string
</v-clicks>

---
layout: default
level: 2
title: While - ejemplos
hideInToc: true
---

# While
## Ejemplos

Resolvamos el mismo ejercicio anterior, pero ahora usando un `while`.

> Haz un algoritmo que le pida al usuario un número (mayor a 0), y luego imprima todos los números desde el 1 hasta el número ingresado por el usuario.

```python
numero_objetivo = int(input())
numero_mostrado = 1

# Mientras el numero mostrado sea menor o igual al numero objetivo
while numero_mostrado <= numero_objetivo:
    # Mostrar el numero mostrado
    print(numero_mostrado)
    # Aumentar el numero mostrado en 1
    numero_mostrado += 1 # Equivalente a numero_mostrado = numero_mostrado + 1
```

Aquí usamos lo que suele llamarse un **contador**, que es una variable que se usa para contar algo. En este caso, el contador es `numero_mostrado`, que cuenta los números que se han mostrado hasta el momento.

---
layout: center
level: 3
title: Ejemplo visualizado
hideInToc: true
---
# Ejemplo visualizado

<iframe width="800" height="500" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=numero_objetivo%20%3D%2010%20%23%20por%20ejempl,%20en%20vez%20de%20int%28input%28%29%29%0Anumero_mostrado%20%3D%201%0A%0A%23%20Mientras%20el%20numero%20mostrado%20sea%20menor%20o%20igual%20al%20numero%20objetivo%0Awhile%20numero_mostrado%20%3C%3D%20numero_objetivo%3A%0A%20%20%20%20%23%20Mostrar%20el%20numero%20mostrado%0A%20%20%20%20print%28numero_mostrado%29%0A%20%20%20%20%23%20Aumentar%20el%20numero%20mostrado%20en%201%0A%20%20%20%20numero_mostrado%20%2B%3D%201%20%23%20Equivalente%20a%20numero_mostrado%20%3D%20numero_mostrado%20%2B%201&codeDivHeight=400&codeDivWidth=350&cumulative=false&curInstr=15&heapPrimitives=nevernest&origin=opt-frontend.js&py=311&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe>

---
layout: two-cols
level: 2
title: While - más ejemplos
hideInToc: true
---

# While
## Ejemplos

Un programa que imprima y simule la suma de los N primeros montos de reembolsos mensuales recurrentes de $300 cada uno.

```python
n = int(input())
contador = 1
while contador <= n:
    print(contador * 300)
    contador += 1
```

Y si queremos mostrar los N primeros pares de sumas de montos de gastos: uno por almuerzos de equipo ($300 cada uno) y otro por transporte ($500 cada uno)?

```python
n = int(input())
contador = 1
while contador <= n:
    print(contador * 300, contador * 500)
    contador += 1
```

::right::

Y mostrar los N primeros pares de sumas de gastos de almuerzos ($300) y transporte ($500). Si la cantidad de gastos es par, mostrar ambos; si no, mostrar gastos alternativos: coffee breaks ($400) y estacionamiento ($600)?

```python
n = int(input())
contador = 1
while contador <= n:
    if (contador * 300 + contador * 500) and contador % 2 == 0:
        print(contador * 300, contador * 500)
    else:
        print(contador * 400, contador * 600)
    contador += 1
```

❓ Ahora supongamos un ejemplo más complejo.

Podríamos querer hacer lo siguiente:

- Trabajar con los N primeros pares de gastos de almuerzos ($300) y transporte ($500).
- Para cada par, normalmente mostraríamos los montos de ambos gastos.
- Sin embargo, si la suma de ambos gastos resulta ser un número par, en vez de mostrar los montos, podriamos querer mostrar un proceso de reembolso por ese total, mostrando los descuentos del total por cada parte reembolsada.
- Luego, continuamos con los siguientes pares de gastos, repitiendo el mismo procedimiento.
- Al finalizar, mostramos la suma total de los gastos de almuerzos.

Para eso, necesitamos saber variables acumuladoras, y ciclos anidados.

---
layout: section
level: 2
title: Variables acumuladoras y ciclos anidados
hideInToc: false
---

# Variables acumuladoras y ciclos anidados
## Manejar datos de forma más compleja

---
layout: default
level: 2
title: Variables acumuladoras
hideInToc: true
---

# Variables acumuladoras

A veces, necesitamos guardar datos de forma más compleja: calcular la suma de ciertos números, o bien, el promedio y/o otras operaciones.
Para eso, necesitamos usar **variables acumuladoras**. Solamente es una forma distinta de llamar a una variable que se usa para acumular datos.

Por ejemplo, calcular un promedio de montos de gastos hasta que el monto ingresado sea `-1.0`

```python {1-2|3-5|6-8|9-11|12-} {lines:true}
# Obtener el primer monto
monto = float(input())
# Inicializar las variables acumuladora
suma_montos = 0
cantidad_montos = 0
# Mientras el monto no sea -1
while monto != -1:
    # Acumular el monto
    suma_montos += monto
    # Acumular la cantidad de montos
    cantidad_montos += 1
    # Obtener el siguiente monto
    monto = float(input())
# Calcular el promedio
promedio = suma_montos / cantidad_montos
# Mostrar el promedio
print(promedio)
```

---
layout: default
level: 2
title: Ejercicio
hideInToc: true
---

## Ejercicio

Supón que tienes que generar un archivo de informe de gastos para varias áreas de una empresa.

Cada área tiene varios gastos, y cada gasto tiene un peso de 120 KB.

El programa debe pedir al usuario la cantidad de áreas, luego para cada área la cantidad de gastos. Una vez que se han ingresado todos los gastos de un área, se debe exportar el archivo de reporte de la siguiente manera:

Si el tamaño del archivo es menor a 1 GB (equivalente a 1024 MB o `1024 * 1024 KB`), se debe imprimir que el archivo se generó con el nombre "xpendit_informe_x_areas_x_gastos.xslx"
Si el tamaño del archivo supera los 1 GB (equivalente a 1024 MB o `1024 * 1024 KB`), se debe avisar al usuario que el archivo es muy grande y deberá pedir un correo a donde se enviará el archivo.
Si el tamaño del archivo supera los 10 GB (equivalente a 10240 MB o `10240 * 1024 KB`), se debe avisar al usuario que el archivo es demasiado grande y no se puede exportar, y que debe contactar a soporte.

---
layout: default
level: 2
title: Ejercicio
hideInToc: true
---

## Ejemplo de entrada y salida:

```text {1|2-3|4|5-6}{lines:true}
¿Cuántas áreas quieres reportar? 2
¿Cuántos gastos tiene el área #1? 2
¿Cuántos gastos tiene el área #2? 2
Total de gastos: 4
El peso total del archivo es de 480 KB, se exportará en un solo archivo.
Archivo exportado con nombre xpendit_informe_2_areas_4_gastos.xslx
```

```text {1|2-6|7|8-10|11}{lines:true}
¿Cuántas áreas quieres reportar? 5
¿Cuántos gastos tiene el área #1? 1000
¿Cuántos gastos tiene el área #2? 4570
¿Cuántos gastos tiene el área #3? 1000
¿Cuántos gastos tiene el área #4? 1345
¿Cuántos gastos tiene el área #5? 5123
Total de gastos: 13038
El peso total del archivo es de 13038 KB, lo que supera el límite de 1 GB.
Por favor, ingresa un correo a donde se enviará el archivo:
Correo: juan@acme.com
Archivo exportado con nombre xpendit_informe_5_areas_13038_gastos.xslx
```

```text {1|2-3|4|5-6}{lines:true}
¿Cuántas áreas quieres reportar? 2
¿Cuántos gastos tiene el área #1? 45875
¿Cuántos gastos tiene el área #2? 234509867
Total de gastos: 234555742
El peso total del archivo es de 28146689040 KB, lo que supera el límite de 10 GB.
Por favor, contacta a soporte.
```

---
layout: default
level: 2
title: Ejercicio resuelto
hideInToc: true
---

```python {1-4|5-7|8-13|14-17|19-21|23-25|23-29|23-32}{lines: true, maxHeight: '450px'}
# Pedir la cantidad de áreas a ingresar
tamano_gasto_kb = 120
n_areas = int(input("¿Cuántas áreas quieres reportar? "))

total_gastos = 0
area_num = 1
primer_area_gastos = 0
while area_num <= n_areas:
    n_gastos = int(input(f"¿Cuántos gastos tiene el área #{area_num}? "))
    if area_num == 1:
        primer_area_gastos = n_gastos
    total_gastos += n_gastos
    area_num += 1

peso_total_kb = total_gastos * tamano_gasto_kb

print(f"Total de gastos: {total_gastos}")

# Límites en KB
gb_1_kb = 1024 * 1024
gb_10_kb = 10240 * 1024

if peso_total_kb < gb_1_kb:
    print(f"El peso total del archivo es de {peso_total_kb} KB, se exportará en un solo archivo.")
    print(f"Archivo exportado con nombre xpendit_informe_{n_areas}_areas_{primer_area_gastos}_gastos.xslx")
elif peso_total_kb < gb_10_kb:
    print(f"El peso total del archivo es de {peso_total_kb} KB, lo que supera el límite de 1 GB.")
    correo = input("Por favor, ingresa un correo a donde se enviará el archivo:\nCorreo: ")
    print(f"Archivo exportado con nombre xpendit_informe_{n_areas}_areas_{primer_area_gastos}_gastos.xslx")
else:
    print(f"El peso total del archivo es de {peso_total_kb} KB, lo que supera el límite de 10 GB.")
    print("Por favor, contacta a soporte.")
```

---
layout: default
level: 2
title: Ciclos anidados
hideInToc: true
---

# Ciclos anidados

A veces, vamos a querer repetir una acción, en cada paso de un ciclo. Para ello podemos anidar ciclos todas las veces que queramos. Hacer esto es igual que al anidar `if`s, pero en vez de usar `if` usamos `while`.

Algunos ejemplos:

- Los turnos de un juego, donde cada jugador tiene un turno, y cada turno tiene varias acciones.
- Los días de la semana, donde cada día tiene varias horas, y cada hora tiene varios minutos.

Ejemplo en código:

```python {1|2|3-4|5-6|7|6|8|4|9|2|10} {lines:true}
... # Algoritmo antes
while CONDICION_1:
    instruccion_1_antes
    while CONDICION_2:
        instruccion_2_antes
        while CONDICION_3:
            instruccion_3
        instruccion_2_despues
    instrucción_1_despues
... # Algoritmo después
```

---
layout: default
level: 2
title: Ejemplo avanzado
hideInToc: false
---

# Ejemplo avanzado

### Ejercicio: Aprobación de Gastos según Políticas

**Contexto:**

En una empresa, recibes solicitudes de gastos de diferentes empleados. Cada solicitud tiene un monto, una categoría y un nivel de urgencia. Debes aprobar la mejor solicitud de cada empleado, priorizando primero la urgencia (mayor es mejor), luego el monto (menor es mejor), y finalmente la categoría (el orden de prioridad es: Viajes > Insumos > Alimentación).

---
layout: default
level: 2
title: Ejemplo avanzado
hideInToc: false
---

**Entradas:**

- Un número entero `N` que representa el número de empleados.
- Para cada empleado:
  - Un número entero que indica cuántas solicitudes de gasto presenta ese empleado.
  - Para cada solicitud: tres datos: monto (entero), categoría (texto: "Viajes", "Insumos" o "Alimentación"), urgencia (entero, mayor es más urgente).

**Salidas:**

- Por cada empleado, se debe imprimir "Solicitud aprobada:", seguido de una solicitud con los detalles de esta y del empleado que la presentó (empleado #, monto, categoría, urgencia).
- Al final, se debe imprimir "Total gastado:", seguido del total gastado en todas las solicitudes aprobadas.

**Restricciones:**

- monto y urgencia son enteros positivos
- categoría es un texto válido
- Viajes > Insumos > Alimentación

---
layout: default
level: 2
title: Ejemplo avanzado
hideInToc: true
---

**Ejemplo:**

```text
¿Cuántos empleados hay? 2
¿Cuántas solicitudes tiene el empleado #1? 2
¿Cuál es el monto de la solicitud #1 del empleado #1? 500
¿Cuál es la categoría de la solicitud #1 del empleado #1? Viajes
¿Cuál es la urgencia de la solicitud #1 del empleado #1? 3
¿Cuál es el monto de la solicitud #2 del empleado #1? 700
¿Cuál es la categoría de la solicitud #2 del empleado #1? Insumos
¿Cuál es la urgencia de la solicitud #2 del empleado #1? 2
Solicitud aprobada: Empleado 1: 500 Viajes 3
¿Cuántas solicitudes tiene el empleado #2? 3
¿Cuál es el monto de la solicitud #1 del empleado #2? 400
¿Cuál es la categoría de la solicitud #1 del empleado #2? Alimentación
¿Cuál es la urgencia de la solicitud #1 del empleado #2? 3
¿Cuál es el monto de la solicitud #2 del empleado #2? 300
¿Cuál es la categoría de la solicitud #2 del empleado #2? Viajes
¿Cuál es la urgencia de la solicitud #2 del empleado #2? 2
¿Cuál es el monto de la solicitud #3 del empleado #2? 400
¿Cuál es la categoría de la solicitud #3 del empleado #2? Insumos
¿Cuál es la urgencia de la solicitud #3 del empleado #2? 3
Solicitud aprobada: Empleado 2: 400 Insumos 3
Total gastado: 900
```

---
layout: default
level: 2
title: Ejemplo avanzado
hideInToc: true
---

### Modelamiento y explicación

En este problema, queremos aprobar la mejor solicitud de gasto para cada empleado según tres criterios, en orden de prioridad:

1. **Urgencia**: Se prefiere la solicitud con mayor urgencia.
2. **Monto**: Si hay empate en urgencia, se prefiere la de menor monto.
3. **Categoría**: Si hay empate en urgencia y monto, se prefiere la categoría con mayor prioridad: Viajes > Insumos > Alimentación.

Para resolverlo, para cada empleado leemos todas sus solicitudes y vamos guardando la mejor encontrada hasta el momento, comparando cada nueva solicitud con la mejor actual según los criterios anteriores.

**Imprimimos el resultado de cada empleado inmediatamente después de encontrar su mejor solicitud.**

---
layout: default
level: 2
title: Ejemplo avanzado
hideInToc: true
---

### Solución:

```python {1-9|9-11|9-19|19-23|24-30|31-40|41-46|19,47|48-50|9,51|52-53|all}{lines:true, maxHeight: '450px'}
# Leer la cantidad de empleados
cantidad_empleados = int(input())

# Inicializar el total gastado en todas las solicitudes aprobadas
suma_total_gastos = 0

# Procesar cada empleado uno por uno
empleado_actual = 1
while empleado_actual <= cantidad_empleados:
    # Leer la cantidad de solicitudes de este empleado
    cantidad_solicitudes = int(input(f"¿Cuántas solicitudes tiene el empleado #{empleado_actual}? "))
    # Inicializar variables para la mejor solicitud encontrada
    mejor_urgencia = -1
    mejor_monto = 0
    mejor_categoria = ""
    mejor_prioridad_categoria = 0
    # Procesar cada solicitud de este empleado
    solicitud_actual = 0
    while solicitud_actual < cantidad_solicitudes:
        # Leer los datos de la solicitud
        monto_solicitud = int(input(f"¿Cuál es el monto de la solicitud #{solicitud_actual + 1} del empleado #{empleado_actual}? "))
        categoria_solicitud = input(f"¿Cuál es la categoría de la solicitud #{solicitud_actual + 1} del empleado #{empleado_actual}? ")
        urgencia_solicitud = int(input(f"¿Cuál es la urgencia de la solicitud #{solicitud_actual + 1} del empleado #{empleado_actual}? "))
        # Determinar la prioridad de la categoría
        if categoria_solicitud == "Viajes":
            prioridad_categoria = 3
        elif categoria_solicitud == "Insumos":
            prioridad_categoria = 2
        else:
            prioridad_categoria = 1
        # Decidir si esta solicitud es mejor que la mejor encontrada hasta ahora
        es_mejor = False
        if urgencia_solicitud > mejor_urgencia:
            es_mejor = True
        elif urgencia_solicitud == mejor_urgencia:
            if monto_solicitud < mejor_monto or mejor_urgencia == -1:
                es_mejor = True
            elif monto_solicitud == mejor_monto:
                if prioridad_categoria > mejor_prioridad_categoria:
                    es_mejor = True
        # Si es mejor, actualizar los datos de la mejor solicitud
        if es_mejor:
            mejor_urgencia = urgencia_solicitud
            mejor_monto = monto_solicitud
            mejor_categoria = categoria_solicitud
            mejor_prioridad_categoria = prioridad_categoria
        solicitud_actual += 1
    # Imprimir la mejor solicitud aprobada para este empleado
    print(f"Empleado {empleado_actual}: {mejor_monto} {mejor_categoria} {mejor_urgencia}")
    suma_total_gastos += mejor_monto
    empleado_actual += 1
# Imprimir el total gastado en todas las solicitudes aprobadas
print(f"Total gastado: {suma_total_gastos}")
```

---
layout: center
level: 1
title: Spoiler while
hideInToc: true
---

# Coming soon...

En el último ejemplo, usamos un `while` para iterar sobre los empleados, y otro `while` para iterar sobre las solicitudes de cada empleado. Esto es un ejemplo de un ciclo anidado, que es un ciclo dentro de otro ciclo. Pero, ¿no sabíamos exactamente cuántas veces se iba a repetir el ciclo?
¿Es necesario repetir el ciclo infinitamente hasta que se cumpla la condición de término? ¿No podemos repetirlo un número específico de veces?

Para eso el `for`, que comenzaremos a ver en la próxima clase.
