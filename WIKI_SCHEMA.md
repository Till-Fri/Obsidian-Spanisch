# Spanish Learning Wiki Schema

## Objective
Transform raw Spanish input (texts, audio, conversations) into a compounding knowledge base of grammar and vocabulary, supporting the transition from B1 to B2.1.

## User Profile
- **Current Level:** B1
- **Target Level:** B2.1
- **Current Focus:** Full grammar recap (all tenses) with a deep dive into Subjuntivo (Imperfecto and Futuro).

## Layer Definitions
1. **Raw Layer (`/raw/`)**: Immutable source files. I read these but never edit them.
2. **Wiki Layer (`/wiki/`)**: The synthesized knowledge. I own this layer.
3. **Schema Layer**: This document.

## Workflows

### 📥 Ingestion Flow
When a new source is provided:
1. **Log**: Add entry to `wiki/log.md` (e.g., `## [YYYY-MM-DD] ingest | Topic/Source`).
2. **Analyze**:
    - **B1 Review Vocab**: Extract key B1 level words that are essential for the "Recap" phase.
    - **B2-bridge Vocab**: Extract nuanced adjectives, idiomatic expressions, and academic verbs.
    - **Tense Mapping**: Identify ALL tenses used. Extract the usage as a "Recap Example."
    - **Subjunctive Focus**: Specifically flag and analyze all uses of Subjuntivo (especially Imperfecto and Futuro).
3. **Update Wiki**:
    - **Grammar Pages**: Update the relevant page (e.g., `wiki/grammar/Preterito.md` for recap).
    - **Vocab Pages**: Update relevant theme pages. Separate "B1 Recap" from "B2 Expansion" sections within the page.
    - Create new pages if the topic is novel.
4. **Index**: Add/update entries in `wiki/index.md`.

### ❓ Query Flow
When asked about a word or rule:
1. Search the `/wiki/` folder first.
2. Provide the answer with a link to the specific wiki page.
3. If the answer reveals a gap in the wiki, create a new page or update an existing one immediately.

### 🧹 Lint Flow (Periodic)
- Identify "Orphan" vocabulary.
- Suggest review topics based on the `log.md`.
- **Tense Audit**: Identify which grammar pages haven't been "recapitulated" recently.

## Formatting Conventions
- **Links**: MUST use double brackets for all internal references: `[[Page Name]]`.
- **Vocabulary Entries**: `Word (Gender/Plural) - Translation [Level: B1/B2] [Example Sentence]`
- **Grammar Entries**: Use clear headings for "Rule", "Exceptions", and "Usage Examples (Recaps)".


