# Bitacora de tecnicas avanzadas

Laboratorio 07: Tecnicas Avanzadas de Prompting.
Herramienta de IA usada: Claude y Gemini

## Ejercicio 2: Zero-shot, one-shot y few-shot

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|--------------------------|--------------------------------------|
| Zero-shot | 5 | Tabla con columnas #, Comentario, Clasificacion, mas explicacion extra | No aplica (una sola respuesta) |
| One-shot | 5 | Lista numerada: "texto" -> Etiqueta | No aplica (una sola respuesta) |
| Few-shot | 5 | Lista sin numeros: "texto" -> Etiqueta, igual a los ejemplos | Si |

## Ejercicio 3: Chain of Thought

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
|--------|---------------------|------------------------------|--------------------|
| Directo | 318.60 | No | Si |
| Paso a paso | Precio con descuento: 120 x 0.75 = 90. Precio con IGV: 90 x 1.18 = 106.20. Total x 3 unidades: 106.20 x 3 = 318.60 | Si | Si |

## Ejercicio 4: Role prompting

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---------|----------------------------------|---------------------------|----------------------|
| A. Sin rol | Mixto, definicion general | No | A cualquier lector |
| B. Rol docente | Sencillo, con analogias (una caja con etiqueta) | Ejemplos cotidianos, sin codigo | Estudiantes que nunca programaron |
| C. Rol senior | Tecnico (tipo de dato, memoria, alcance) | Codigo Java | Desarrolladores con experiencia |

## Ejercicio 5: Descomposicion

Pedido por pasos:
- Paso 1: la IA listo 5 requisitos principales del sistema.
- Paso 2: con esos requisitos, diseno las clases necesarias con sus atributos y tipos de dato.
- Paso 3: escribio el codigo Java de la clase Producto con atributos, constructor y metodos get/set.
- Paso 4: reviso el codigo y propuso 3 mejoras concretas (validaciones, encapsulamiento, manejo de excepciones).

El resultado por pasos fue mas coherente porque cada respuesta se construyo sobre el contexto de la respuesta anterior, mientras que el pedido unico se quedo en un nivel muy general.

## Ejercicio 6: Prompt estructurado y autocritica

| Que revisar | Cumple (Si/No) |
|---|---|
| Tiene las 4 columnas pedidas | Si |
| Incluye el bloqueo despues de 3 intentos | Si |
| Incluye casos con campos vacios | Si (agregados en la autocritica) |
| Indica que casos agrego en la autocritica | Si |
| Hay algun caso repetido o que no tenga sentido | No |

```text
<rol>Actua como analista de pruebas de software.</rol>
<contexto>Login web con correo y contrasena. La cuenta se bloquea
despues de 3 intentos fallidos.</contexto>
<tarea>Piensa paso a paso que puede fallar y escribe 6 casos de prueba.</tarea>
<formato>Tabla con las columnas: ID, escenario, datos de entrada,
resultado esperado.</formato>

Revisa tu tabla: faltan casos limite como campos vacios, correo sin @
o contrasena con espacios? Agrega los que falten e indica cuales agregaste.
```