# README - Sistema Experto para Diagnóstico de Computadoras

## 1. Descripción General

Este proyecto implementa un Sistema Experto para el diagnóstico de fallas en computadoras utilizando un motor de inferencia basado en encadenamiento hacia adelante (Forward Chaining).

El sistema permite que un usuario responda preguntas relacionadas con síntomas observados en un equipo de cómputo. A partir de esos síntomas, el motor de inferencia analiza las reglas almacenadas en la base de conocimiento y genera uno o varios diagnósticos posibles ordenados según su nivel de confianza.
---
# 3. Ajustes Realizados

Durante la ampliación del sistema se agregaron tres nuevas reglas junto con nuevos síntomas.

---

## Regla R08 - Batería CMOS agotada

### Síntomas agregados

* pierde_hora_fecha
* mensaje_cmos

### Regla

```python
SI enciende
Y pierde_hora_fecha
Y mensaje_cmos

ENTONCES batería CMOS agotada
```

### Justificación

Muchos equipos presentan reinicios constantes de fecha y hora cuando la batería CMOS se encuentra descargada. Además, frecuentemente aparece un mensaje de error relacionado con CMOS durante el arranque.

Esta regla permite diagnosticar un problema común que no estaba contemplado en la versión inicial.

---

## Regla R09 - Problema de Red

### Síntomas agregados

* sin_internet
* wifi_desconectado

### Regla

```python
SI enciende
Y sin_internet
Y wifi_desconectado

ENTONCES problema de red
```

### Justificación

Las fallas de conectividad son uno de los incidentes más frecuentes reportados por usuarios.

La incorporación de esta regla amplía el alcance del sistema hacia problemas de comunicación y acceso a Internet.

---

## Regla R10 - CPU Sobrecargada

### Síntomas agregados

* equipo_lento
* cpu_al_100

### Regla

```python
SI enciende
Y equipo_lento
Y cpu_al_100

ENTONCES CPU sobrecargada
```

### Justificación

El alto consumo de CPU suele generar lentitud generalizada en el sistema.

La regla permite identificar problemas asociados a procesos excesivos, malware o aplicaciones mal optimizadas.

---

# 4. Reflexión

## 1. ¿Cuál es la diferencia principal entre un sistema experto y un programa de software tradicional?

La principal diferencia es que un sistema experto intenta imitar el razonamiento de un especialista humano mediante reglas y conocimiento almacenado. Un programa tradicional normalmente ejecuta instrucciones predefinidas para resolver tareas específicas, mientras que un sistema experto toma decisiones basadas en conocimiento y razonamiento.

---

## 2. ¿Por qué se dice que los sistemas expertos tienen conocimiento separado de su motor de razonamiento? ¿Cuál es la ventaja?

Se dice porque las reglas están almacenadas en la base de conocimiento y el razonamiento ocurre en el motor de inferencia.

La ventaja es que puedo modificar o agregar reglas sin tener que cambiar el motor de inferencia. Esto facilita el mantenimiento, la escalabilidad y la reutilización del sistema.

---

## 3. ¿Qué es la base de hechos y en qué se diferencia de la base de conocimiento?

La base de hechos contiene información temporal relacionada con un caso específico.

La base de conocimiento contiene reglas permanentes creadas por expertos.

La diferencia es que la base de hechos cambia en cada consulta, mientras que la base de conocimiento representa el conocimiento general del dominio.

---

## 4. ¿Qué significa que un sistema experto pueda explicar su razonamiento? ¿Por qué es importante en medicina o derecho?

Significa que el sistema puede mostrar qué reglas utilizó y qué hechos provocaron una conclusión determinada.

Esto es importante en medicina o derecho porque las decisiones pueden afectar significativamente a las personas. Los profesionales necesitan comprender por qué el sistema llegó a una conclusión para validar que la recomendación sea correcta.

---

## 5. ¿Por qué fracasaron comercialmente los sistemas expertos en los años 90?

Considero que fracasaron porque eran costosos de desarrollar y mantener. Además, dependían de reglas construidas manualmente por expertos y tenían dificultades para adaptarse a situaciones nuevas.

Con el avance de otras tecnologías y posteriormente del aprendizaje automático, muchos sistemas expertos dejaron de ser competitivos.

---

## 6. Dada la siguiente regla:

```text
SI (fiebre AND tos) OR perdida_olfato
ENTONCES sospecha_covid
```

Y los hechos:

```text
fiebre = true
tos = false
perdida_olfato = true
```

¿Se activa la regla? ¿Por qué?

Sí se activa.

La expresión tiene un operador OR.

Aunque la condición:

```text
fiebre AND tos
```

es falsa porque tos es falsa, la condición:

```text
perdida_olfato
```

es verdadera.

Como una de las partes conectadas por OR es verdadera, toda la regla se activa.

---

## 7. ¿Cuál es la diferencia entre encadenamiento hacia adelante y hacia atrás? Da un ejemplo real de cada uno.

El encadenamiento hacia adelante comienza con los hechos disponibles y avanza hasta encontrar conclusiones.

Ejemplo:

Un sistema de diagnóstico de computadoras recibe síntomas y genera posibles fallas.

El encadenamiento hacia atrás comienza con una hipótesis y busca evidencias para demostrarla.

Ejemplo:

Un médico sospecha que un paciente tiene una enfermedad específica y solicita pruebas para confirmar o descartar esa hipótesis.

---

## 8. Diseña 3 reglas IF-THEN para asesorar a estudiantes sobre qué lenguaje aprender primero.

### Regla 1

```text
SI objetivo = desarrollo_web
ENTONCES aprender JavaScript
```

### Regla 2

```text
SI objetivo = analisis_datos
ENTONCES aprender Python
```

### Regla 3

```text
SI objetivo = desarrollo_videojuegos
ENTONCES aprender C#
```

---

## 9. Dibuja la red de inferencia correspondiente

```text
                 objetivo=desarrollo_web
                           │
                           ▼
                  aprender JavaScript


                objetivo=analisis_datos
                           │
                           ▼
                    aprender Python


             objetivo=desarrollo_videojuegos
                           │
                           ▼
                      aprender C#
```

---

