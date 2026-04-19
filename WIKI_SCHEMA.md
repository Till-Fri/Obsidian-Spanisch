# Spanish Learning Wiki Schema

## Objective
Transform raw Spanish input (texts, audio, conversations) into a compounding knowledge base of grammar and vocabulary.

## Layer Definitions
1. **Raw Layer (`/raw/`)**: Immutable source files. I read these but never edit them.
2. **Wiki Layer (`/wiki/`)**: The synthesized knowledge. I own this layer.
3. **Schema Layer**: This document.

## Workflows

### 📥 Ingestion Flow
When a new source is provided:
1. **Log**: Add entry to `wiki/log.md` (e.g., `## [YYYY-MM-DD] ingest | Topic/Source`).
2. **Analyze**:
    - Extract **New Vocabulary**: Identify words/phrases the user doesn't know.
    - Identify **Grammar Patterns**: Spot the tenses and structures used.
3. **Update Wiki**:
    - Update the relevant **Grammar page** (e.g., if the text uses the imperfect, update `wiki/grammar/Imperfecto.md`).
    - Update the relevant **Vocabulary page** (e.g., if it's about food, update `wiki/vocabulary/Food.md`).
    - Create new pages if the topic is novel.
4. **Index**: Add/update entries in `wiki/index.md`.

### ❓ Query Flow
When asked about a word or rule:
1. Search the `/wiki/` folder first.
2. Provide the answer with a link to the specific wiki page.
3. If the answer reveals a gap in the wiki, create a new page or update an existing one immediately.

### 🧹 Lint Flow (Periodic)
- Identify "Orphan" vocabulary (words not linked to a grammar rule).
- Suggest review topics based on the `log.md` (e.g., "You haven't updated the 'Subjuntivo' page in 2 weeks").

## Formatting Conventions
- **Links**: Use `[[Page Name]]` for all internal references.
- **Vocabulary Entries**: `Word (Gender/Plural) - Translation [Example Sentence]`
- **Grammar Entries**: Use clear headings for "Rule", "Exceptions", and "Usage Examples".
