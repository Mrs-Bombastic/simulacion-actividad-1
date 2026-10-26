# 🎲 Yahtzee en Python — Simulación mediante el Método de Montecarlo

## 1. Descripción del proyecto

Este proyecto académico consiste en el desarrollo de una aplicación que simula el juego clásico de **Yahtzee para dos jugadores**, utilizando Python como lenguaje de programación.

El juego consiste en lanzar cinco dados convencionales de seis caras, permitiendo hasta tres lanzamientos por turno. Los jugadores pueden conservar determinados dados y utilizar las combinaciones obtenidas para registrar puntuaciones.

Adicionalmente, se implementó un algoritmo basado en el **método de Montecarlo**, que permite ejecutar múltiples simulaciones automáticas, analizar los resultados obtenidos y estudiar el comportamiento de la **Ley de los Grandes Números**.

El desarrollo se realizó principalmente en Google Colab, utilizando bibliotecas de Python para la generación de números aleatorios, la construcción de interfaces interactivas y el análisis estadístico.

## 2. Objetivo general

Desarrollar una aplicación en Python que simule el juego Yahtzee para dos jugadores y permita aplicar el método de Montecarlo para analizar resultados aleatorios y estudiar experimentalmente la Ley de los Grandes Números.

### Objetivos específicos

- Simular el lanzamiento de cinco dados mediante una distribución uniforme discreta.
- Implementar hasta tres lanzamientos por turno.
- Permitir conservar dados seleccionados.
- Gestionar dos jugadores y sus puntuaciones.
- Implementar las trece categorías de puntuación de Yahtzee.
- Ejecutar simulaciones automáticas utilizando Montecarlo.
- Generar estadísticas y gráficas de los resultados.
- Analizar la convergencia de las frecuencias relativas y los promedios acumulados.

## 3. Tecnologías utilizadas

| Tecnología | Descripción |
|---|---|
| Python 3 | Lenguaje de programación principal |
| Google Colab | Entorno de desarrollo y ejecución |
| random | Generación de números pseudoaleatorios |
| collections.Counter | Conteo de valores repetidos |
| ipywidgets | Construcción de la interfaz interactiva |
| NumPy | Procesamiento numérico y simulaciones |
| Pandas | Organización de resultados estadísticos |
| Matplotlib | Visualización gráfica |
| GitHub | Almacenamiento y documentación del proyecto |

## 4. Metodología USA, MODIFICA y CREA

### USA — Comprensión del ejemplo

Inicialmente se analizó el funcionamiento del juego Yahtzee presentado como referencia por el docente.

Se identificaron sus principales características, incluyendo los cinco dados, los lanzamientos, las categorías de puntuación y los turnos de los participantes.

Posteriormente, se desarrolló un primer algoritmo en Python que permitió simular el lanzamiento de cinco dados mediante la función `random.randint(1, 6)`.

```python
import random

def lanzar_dados():
    return [random.randint(1, 6) for _ in range(5)]

dados = lanzar_dados()

print("Resultado:", dados)
print("Suma:", sum(dados))
```

### MODIFICA — Incorporación de funcionalidades

Se amplió la solución inicial mediante las siguientes funcionalidades:

- Control de hasta tres lanzamientos por turno.
- Conservación de dados seleccionados.
- Interfaz gráfica interactiva.
- Registro de puntuaciones.
- Participación de dos jugadores.
- Alternancia automática de turnos.

Para construir la interfaz dentro de Google Colab se utilizó `ipywidgets`.

### CREA — Simulación de Montecarlo

Se desarrolló un algoritmo capaz de ejecutar automáticamente múltiples partidas del juego.

Las principales funciones implementadas fueron:

| Función | Descripción |
|---|---|
| `calcular_puntos()` | Calcula los puntos de una combinación |
| `lanzar_turno()` | Simula hasta tres lanzamientos |
| `jugar_partida()` | Ejecuta una partida automática |
| `simular_montecarlo()` | Ejecuta múltiples partidas y calcula estadísticas |

El algoritmo automático utiliza una estrategia básica de conservación de dados repetidos y selección de la categoría disponible con mayor puntuación inmediata.

## 5. Funcionamiento del juego

### Reglas generales

El juego utiliza cinco dados de seis caras.

Cada jugador puede realizar un máximo de tres lanzamientos durante su turno y seleccionar los dados que desea conservar.

Al finalizar, debe elegir una categoría disponible para registrar su puntuación.

La partida consta de trece turnos por jugador.

### Categorías de puntuación

| Categoría | Puntuación |
|---|---|
| Unos | Suma de los dados con valor 1 |
| Doses | Suma de los dados con valor 2 |
| Treses | Suma de los dados con valor 3 |
| Cuatros | Suma de los dados con valor 4 |
| Cincos | Suma de los dados con valor 5 |
| Seises | Suma de los dados con valor 6 |
| Trío | Suma de los cinco dados si hay al menos tres iguales |
| Póker | Suma de los cinco dados si hay al menos cuatro iguales |
| Full house | 25 puntos |
| Escalera corta | 30 puntos |
| Escalera larga | 40 puntos |
| Suerte | Suma de los cinco dados |
| Yahtzee | 50 puntos si los cinco dados son iguales |

Se contempla la bonificación de 35 puntos cuando la sección superior alcanza al menos 63 puntos.

**Nota:** las reglas especiales de comodín y asignación obligatoria en Yahtzees adicionales requieren completar su validación antes de considerar la implementación una reproducción totalmente fiel del reglamento clásico.

## 6. Método de Montecarlo

El método de Montecarlo consiste en utilizar simulaciones aleatorias repetidas para estimar resultados y analizar su comportamiento estadístico.

En este proyecto se realizaron simulaciones automáticas de partidas de Yahtzee, así como experimentos independientes sobre la distribución de las caras de un dado.

Cada cara del dado presenta una probabilidad teórica uniforme:

**P(X = k) = 1/6 ≈ 16,667 %**

El promedio teórico de un dado equilibrado es:

**E(X) = (1 + 2 + 3 + 4 + 5 + 6) / 6 = 3,5**

## 7. Resultados obtenidos

Se realizaron experimentos de 1.000 y 10.000 partidas automáticas, observando la evolución de los promedios acumulados de puntuación de ambos jugadores.

También se ejecutaron 100.000 lanzamientos independientes para estudiar la Ley de los Grandes Números.

### Resultados de convergencia

| Lanzamientos | Probabilidad observada de la cara 6 | Promedio observado |
|---:|---:|---:|
| 100 | 0,14000 | 3,64000 |
| 1.000 | 0,15900 | 3,48800 |
| 10.000 | 0,16250 | 3,47520 |
| 100.000 | 0,16586 | 3,49982 |
| Valor teórico | 0,16667 | 3,50000 |

Los resultados muestran que, al aumentar el número de lanzamientos, las estimaciones observadas tienden a aproximarse a los valores teóricos.

Con 100.000 lanzamientos, la frecuencia relativa de la cara seis alcanzó el 16,586 %, mientras que el promedio observado fue de 3,49982.

Este comportamiento es consistente con la Ley de los Grandes Números.

## 8. Estructura del repositorio

```text
Yahtzee-Montecarlo-Python/
│
├── README.md
├── Yahtzee_Montecarlo.ipynb
├── requirements.txt
│
├── documentacion/
│   └── Informe_Montecarlo.pdf
│
└── imagenes/
    ├── juego_yahtzee.png
    ├── simulacion_1000.png
    ├── simulacion_10000.png
    └── convergencia_montecarlo.png
```

Esta es la estructura prevista para la entrega. Los archivos y carpetas deben incorporarse efectivamente al repositorio antes de considerarlo completo.

## 9. Instalación y ejecución

### Opción principal: Google Colab

1. Ingresar a https://colab.research.google.com/
2. Seleccionar **Archivo → Subir cuaderno**.
3. Cargar `Yahtzee_Montecarlo.ipynb`.
4. Ejecutar las celdas de Python en orden.
5. Utilizar la interfaz interactiva del juego.
6. Ejecutar los experimentos de Montecarlo.
7. Analizar las tablas y las gráficas generadas.

### Dependencias

Las bibliotecas principales utilizadas son:

```text
numpy
pandas
matplotlib
ipywidgets
```

Las bibliotecas `random` y `collections` forman parte de la biblioteca estándar de Python.

## 10. Validación y limitaciones

Se realizaron pruebas manuales para verificar el lanzamiento de los dados, el cambio de turnos, el registro de puntuaciones y la ejecución de las simulaciones.

El proyecto utiliza números pseudoaleatorios y semillas para facilitar la reproducibilidad de los experimentos.

La estrategia de los jugadores automáticos es heurística y no representa necesariamente la estrategia óptima de Yahtzee.

La versión desarrollada funciona dentro del cuaderno de Google Colab. Una posible mejora futura consiste en desarrollar una aplicación web independiente mediante Streamlit.

## 11. Conclusiones

El desarrollo del juego Yahtzee permitió aplicar conceptos de programación, estructuras de datos, probabilidad y simulación computacional utilizando Python.

El método de Montecarlo permitió generar múltiples resultados aleatorios y analizar el comportamiento de las puntuaciones obtenidas.

Los experimentos mostraron que, al incrementar el tamaño de la muestra, los promedios acumulados y las frecuencias relativas tienden a estabilizarse alrededor de sus valores esperados.

De esta manera, el proyecto permitió comprender experimentalmente la Ley de los Grandes Números y reconocer la utilidad de Python para el análisis de fenómenos probabilísticos.

## 12. Referencias bibliográficas

- Python Software Foundation. [Documentación oficial de Python](https://docs.python.org/3/)
- NumPy Developers. [Documentación de NumPy](https://numpy.org/doc/stable/)
- Pandas Development Team. [Documentación de Pandas](https://pandas.pydata.org/docs/)
- Matplotlib Development Team. [Documentación de Matplotlib](https://matplotlib.org/stable/)
- Hasbro. [Reglas oficiales de Yahtzee](https://instructions.hasbro.com/en-us/instruction/yahtzee)
- Solitaired. [Juego Yahtzee](https://solitaired.com/yahtzee)
- Google. [Google Colab](https://colab.research.google.com/)

## 13. Autores

**Proyecto académico desarrollado por:**

- KAREN LORENA VERGARA SUAREZ
- EULISES MOREALES
- ANDRES JARAMILLO

**Institución:** IU Digital de Antioquia

**Fecha:** Octubre de 2026

**Asignatura:** [Nombre de la asignatura]
