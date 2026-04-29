# Schema de la Wiki de Español

## Objetivo
Transformar fuentes en español en dos capas complementarias:
- una wiki legible para comprensión, repaso y conexiones
- una capa separada de `Karteikarten/` para exportación selectiva a Anki

La wiki es la capa de referencia. `Karteikarten/` es la capa de memorización.

## Perfil del usuario
- **Nivel actual:** B1
- **Objetivo:** B2.1
- **Foco actual:** repaso de tiempos verbales, subjuntivo y expansión de vocabulario
- **Lenguas de trabajo:** español + alemán

## Capas
1. **Capa raw (`/raw/`)**: fuentes originales e inmutables.
2. **Capa wiki (`/wiki/`)**: notas legibles de gramática y vocabulario.
3. **Capa de tarjetas (`/Karteikarten/`)**: tarjetas curadas para Anki.
4. **Schema**: este documento.

## Estructura

### Wiki
- `wiki/grammar/`
- `wiki/vocabulary/`
- `wiki/entities/`
- `wiki/index.md`
- `wiki/log.md`

### Karteikarten
- `Karteikarten/Grammatik/`
- `Karteikarten/Vokabeln/`
- `Karteikarten/index.md`

## Flujo de trabajo

### 1. Ingesta
Cuando entra una fuente nueva:
1. guardarla en `raw/` sin editarla
2. añadir una entrada a `wiki/log.md`
3. analizar:
   - vocabulario B1 de repaso
   - vocabulario puente hacia B2
   - tiempos verbales presentes en la fuente
   - usos relevantes de subjuntivo
4. **escanear duplicados:** antes de añadir vocabulario nuevo, buscar la palabra en `wiki/vocabulary/` y `Karteikarten/Vokabeln/` para evitar repeticiones innecesarias

### 2. Actualización de la wiki
La wiki sirve para entender, organizar y revisar.

#### Gramática
Las páginas de gramática deben contener:
- uso principal
- contrastes importantes
- una forma modelo cuando aporte valor
- ejemplos agrupados por fuente
- enlaces a páginas relacionadas

#### Vocabulario
Las páginas de vocabulario deben contener:
- agrupación temática o funcional
- colocaciones y patrones con preposición
- ejemplos breves y claros
- notas de uso cuando haga falta
- enlaces a gramática relacionada cuando ayude

#### Entidades y preparación
`wiki/entities/` contiene notas de apoyo que no son estrictamente gramática ni listas de vocabulario:
- planes de preparación
- obras, autores o textos de referencia
- dossiers breves sobre temas reutilizables

Estas páginas deben enlazar hacia `wiki/grammar/` y `wiki/vocabulary/` cuando haya contenido lingüístico reutilizable.

### 3. Destilación a tarjetas
Solo `Karteikarten/` se exporta a Anki.

Reglas:
- las tarjetas están pensadas para aprendizaje humano, no para compresión máxima de información
- añadir solo tarjetas de alto valor
- preferir una sola idea por tarjeta
- priorizar tarjetas útiles para producción activa
- añadir una frase breve como apoyo cuando mejore el recuerdo
- evitar dividir una misma idea en varias tarjetas casi idénticas
- usar contraste y contraejemplos cuando eso evite respuestas automáticas por patrón
- no convertir automáticamente toda la wiki en tarjetas

#### Vocabulario
- preguntar siempre en ambas direcciones:
  - alemán -> español
  - español -> alemán
- mantener la misma frase de apoyo cuando ayude al recuerdo
- preferir una traducción principal por tarjeta; si hace falta, incluir hasta 3 significados cercanos
- si una palabra tiene varias acepciones, usar solo las que encajan con el ejemplo de la fuente o con el uso directamente relevante
- evitar listas amplias de significados no relacionados

#### Gramática
- preferir tarjetas de decisión, contraste y producción
- si una regla se aprende mejor con oposición, incluir un contraejemplo en la misma tarjeta
- evitar series largas de tarjetas que solo repitan "aquí va subjuntivo" sin contraste real

### 4. Índices
- `wiki/index.md` = mapa de la capa de referencia
- `Karteikarten/index.md` = mapa de la capa exportable
- cuando se ingieren muchos archivos raw a la vez, el índice debe enlazar tanto las páginas wiki creadas como las fuentes raw principales

## Convenciones de formato

### Generales
- usar enlaces de Obsidian con formato de doble corchete
- mantener la vault en español + alemán
- no mezclar inglés en títulos, nombres de notas o secciones

### Wiki
- escribir para legibilidad primero
- no usar sintaxis de exportación como formato principal
- se permiten listas, contrastes, notas y ejemplos completos
- los exports grandes de RemNote (`Grammatik`, `Spanisch`) se usan como fuente de comprobación, no como página wiki copiada en bloque

#### Plantilla de página de vocabulario
```markdown
# tema-en-minusculas

## panorama
Contexto breve y link a la fuente.

## sección temática 1
- `palabra`: Traducción alemana
  Ej.: `Frase de ejemplo de la fuente.`

## gramática relacionada
- PaginaDeGramatica
```

### Karteikarten
- usar `# Obsidian_to_Anki` en archivos exportables
- usar `::` solo en `Karteikarten/`
- formato preferido:
  - vocabulario: `prompt en alemán :: respuesta en español`
  - vocabulario inverso: `prompt en español :: respuesta en alemán`
  - gramática: `pregunta o pista en alemán :: forma o regla en español`
- se puede añadir una línea breve de ejemplo con `<br>Ej.: ...`
- para respuestas largas, listas, explicaciones o conjugaciones completas se puede usar formato multilínea `START ... END`
- no poner comentarios `<!--ID: ...-->` manualmente fuera de `Karteikarten/`; esos IDs pertenecen a tarjetas exportables

#### Plantilla de archivo de vocabulario (Karteikarten)
```markdown
# Obsidian_to_Anki
# tema-en-minusculas

prompt en alemán :: respuesta en español<br>Ej.: ... [[Fuente]]

respuesta en español :: prompt en alemán<br>Ej.: ... [[Fuente]]
```

#### Plantilla de tarjeta de gramática (decisión/contraste, 1 línea)
```markdown
Welche Form passt? `Oración con hueco.` / Gegenbeispiel: `Oración contrastante.` :: respuesta correcta / respuesta incorrecta<br>Explicación breve en alemán. [[Fuente]]
```

#### Plantilla de tarjeta multilínea (START...END)
Usar esta opción cuando una respuesta de una línea sería difícil de leer:
- explicaciones largas
- contrastes con varios ejemplos
- listas de desencadenantes
- conjugaciones completas con `yo, tú, él/ella, nosotros, vosotros, ellos`

```markdown
START
Basic
Front: Pregunta o pista en alemán
Back: Explicación o regla en español (puede incluir listas, contrastes, ejemplos)

- punto 1
- punto 2

Ejemplo:
`Frase de ejemplo.`
END
```

#### Plantilla de conjugación completa (multilínea)
```markdown
START
Basic
Front: Konjugiere `verbo` im tiempo: yo, tú, él/ella, nosotros, vosotros, ellos
Back:
- yo: forma
- tú: forma
- él/ella/usted: forma
- nosotros: forma
- vosotros: forma
- ellos/ellas/ustedes: forma

Nota breve sobre uso o irregularidad.
END
```

## Regla de exportación
`Obsidian_to_Anki` debe escanear solo `/Karteikarten/`.

## Regla de consulta
Cuando se pregunte por una palabra o una regla:
1. buscar primero en `/wiki/`
2. responder con enlace a la nota correspondiente
3. usar `Karteikarten/` solo si la pregunta trata sobre memorización o tarjetas
