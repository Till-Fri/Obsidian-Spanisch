# Schema de la Wiki de Español

## Objetivo
Transformar input bruto en español, como textos, audio o conversaciones, en dos capas complementarias:
- una wiki legible para comprensión, repaso y conexiones
- una capa separada de `Karteikarten/` para exportación selectiva a Anki

La wiki es la capa de referencia. `Karteikarten/` es la capa de memorización.

## Perfil del usuario
- **Nivel actual:** B1
- **Objetivo:** B2.1
- **Foco actual:** repaso completo de los tiempos verbales, profundización en el subjuntivo y expansión de vocabulario
- **Lenguas de trabajo:** español + alemán

## Capas
1. **Capa raw (`/raw/`)**: fuentes originales e inmutables.
2. **Capa wiki (`/wiki/`)**: notas legibles de gramática y vocabulario.
3. **Capa de tarjetas (`/Karteikarten/`)**: tarjetas curadas para Anki.
4. **Capa schema**: este documento.

## Estructura actual

### Wiki
- `wiki/grammar/Presente.md`
- `wiki/grammar/Preterito Perfecto.md`
- `wiki/grammar/Preterito-Indefinido.md`
- `wiki/grammar/Subjuntivo.md`
- `wiki/vocabulary/Deporte-y-Negocios.md`
- `wiki/vocabulary/Noticias-y-Politica.md`
- `wiki/vocabulary/Guerra-y-Geopolitica.md`
- `wiki/index.md`
- `wiki/log.md`

### Karteikarten
- `Karteikarten/Grammatik/Basiszeiten.md`
- `Karteikarten/Grammatik/Subjuntivo.md`
- `Karteikarten/Vokabeln/Deporte-y-Negocios.md`
- `Karteikarten/Vokabeln/Noticias-y-Politica.md`
- `Karteikarten/Vokabeln/Guerra-y-Geopolitica.md`
- `Karteikarten/index.md`

## Flujo de trabajo

### 1. Ingesta
Cuando entra una fuente nueva:
1. Añadir una entrada a `wiki/log.md`.
2. Analizar:
   - vocabulario B1 de repaso
   - vocabulario puente hacia B2
   - tiempos verbales presentes en la fuente
   - usos relevantes de subjuntivo
3. Archivar la fuente en `raw/` sin editarla.

### 2. Actualización de la wiki
La wiki debe servir para entender y revisar, no para exportar tarjetas.

#### Gramática
Las páginas de gramática deben contener:
- uso principal
- señales o contrastes importantes
- una forma modelo cuando aporte valor
- ejemplos agrupados por fuente
- enlaces a páginas relacionadas

#### Vocabulario
Las páginas de vocabulario deben contener:
- agrupación temática o funcional
- colocaciones y patrones con preposición
- ejemplos breves y claros
- notas de uso cuando una palabra lo merezca
- enlaces a gramática relacionada cuando ayude

### 3. Destilación a tarjetas
Solo `Karteikarten/` se exporta a Anki.

Reglas:
- añadir solo tarjetas de alto valor
- preferir una sola idea por tarjeta
- priorizar tarjetas útiles para producción activa
- añadir una frase breve como apoyo cuando mejore el recuerdo
- no convertir automáticamente toda la wiki en tarjetas

### 4. Índices
- `wiki/index.md` = mapa de la capa de referencia
- `Karteikarten/index.md` = mapa de la capa exportable

## Convenciones de formato

### Generales
- usar enlaces de Obsidian con `[[Page Name]]`
- mantener la vault en español + alemán
- evitar mezclar inglés en títulos, nombres de notas o secciones

### Wiki
- escribir para legibilidad primero
- no usar sintaxis de exportación como formato principal
- se permiten listas, contrastes, notas y ejemplos completos

### Karteikarten
- usar `# Obsidian_to_Anki` en archivos exportables
- usar `::` solo en `Karteikarten/`
- formato preferido:
  - vocabulario: `prompt en alemán :: respuesta en español`
  - gramática: `pregunta o pista en alemán :: forma o regla en español`
- se puede añadir una línea breve de ejemplo en el reverso con `<br>Ej.: ...`

## Regla de exportación
`Obsidian_to_Anki` debe escanear solo `/Karteikarten/`.

## Regla de consulta
Cuando se pregunte por una palabra o una regla:
1. buscar primero en `/wiki/`
2. responder con enlace a la nota correspondiente
3. usar `Karteikarten/` solo si la pregunta trata sobre memorización o tarjetas
