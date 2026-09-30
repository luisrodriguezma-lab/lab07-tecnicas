# Tarea: Mi prompt avanzado

## Tarea elegida

Generar casos de prueba para un formulario de registro de usuarios (nombre, correo, contrasena, confirmar contrasena).

## Version 1: prompt basico

```text
Dame casos de prueba para un formulario de registro de usuarios.
```

Que le falto: la respuesta fue generica, sin formato de tabla, sin cubrir casos limite especificos del formulario (contrasenas que no coinciden, correo invalido, campos vacios).

## Version 2

```text
Actua como analista de pruebas de software senior.
El formulario de registro tiene los campos: nombre, correo, contrasena
y confirmar contrasena. La contrasena debe tener minimo 8 caracteres.
Escribe 6 casos de prueba en una tabla con las columnas: ID, escenario,
datos de entrada, resultado esperado.
```

Tecnica agregada: role prompting (rol especifico) + prompt estructurado (formato de tabla definido) + contexto del formulario. Mejora: la respuesta ya vino en tabla, con casos mas relevantes al contexto real del formulario.

## Version 3: prompt final

```text
<rol>Actua como analista de pruebas de software senior especializado en formularios web.</rol>
<contexto>Formulario de registro con los campos: nombre, correo, contrasena
y confirmar contrasena. La contrasena debe tener minimo 8 caracteres,
al menos una mayuscula y un numero. El correo debe ser unico en el sistema.</contexto>
<tarea>Piensa paso a paso que puede fallar en cada campo y escribe 8 casos
de prueba que cubran casos validos, invalidos y limite.</tarea>
<formato>Tabla con las columnas: ID, escenario, datos de entrada, resultado esperado.</formato>

Revisa tu tabla: falto algun caso limite como correo ya registrado,
contrasenas que no coinciden, o campos con solo espacios en blanco?
Agrega los que falten e indica cuales agregaste.
```

## Tecnicas usadas en el prompt final

| Parte del prompt | Tecnica |
|---|---|
| `<rol>Actua como analista de pruebas...</rol>` | Role prompting |
| `<contexto>Formulario de registro con los campos...</contexto>` | Prompt estructurado (etiquetas) |
| `<tarea>Piensa paso a paso que puede fallar...</tarea>` | Chain of Thought aplicado a la generacion de casos |
| Mensaje final "Revisa tu tabla: falto algun caso limite..." | Autocritica |

## Evaluacion del resultado

| Que revisar | Cumple (Si/No) |
|---|---|
| Tiene las 4 columnas pedidas | Si |
| Cubre casos validos, invalidos y limite | Si |
| Incluye el caso de correo duplicado | Si (agregado en la autocritica) |
| Indica que casos agrego en la autocritica | Si |

## Por que elegi estas tecnicas

Elegi role prompting porque un formulario de registro necesita un enfoque tecnico de quien realmente prueba software, no una explicacion generica. El prompt estructurado con etiquetas evita que el contexto (reglas de la contrasena, unicidad del correo) se mezcle con la instruccion de la tarea. Combine esto con una version de Chain of Thought orientada a "pensar que puede fallar" en lugar de solo pedir casos al azar, y cerre con autocritica porque, igual que en el Ejercicio 6, la primera tabla de la IA casi nunca cubre todos los casos limite por si sola.