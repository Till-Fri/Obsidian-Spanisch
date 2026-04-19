# Spanish Learning Wiki Schema

## Objective
Transform raw Spanish input (texts, audio, conversations) into a compounding knowledge base of grammar and vocabulary, supporting the transition from B1 to B2.1.

## User Profile
- **Current Level:** B1
- **Target Level:** B2.1
- **Current Focus:** Full grammar recap (all tenses) with a deep dive into Subjuntivo (Imperfecto and Futuro).
- **Native Language:** German (Learning Spanish $\rightarrow$ German).

## Layer Definitions
1. **Raw Layer (`/raw/`)**: Immutable source files. I read these but never edit them.
2. **Wiki Layer (`/wiki/`)**: The synthesized knowledge. I own this layer.
3. **Schema Layer**: This document.

## Workflows

### 📥 Ingestion Flow
When a new source is provided:
1. **Log**: Add entry to `wiki/log.md` (e.g., `## [YYYY-MM-DD] ingest | Topic/Source`).
2. **Analyze**:
    - **B1 Review Vocab**: Extract key B1 level words.
    - **B2-bridge Vocab**: Extract nuanced adjectives, idiomatic expressions, and academic verbs.
    - **Tense Mapping**: Identify ALL tenses used for "Recap Examples."
    - **Subjunctive Focus**: Specifically flag and analyze all uses of Subjuntivo.
3. **Update Wiki**:
    - **Grammar Pages**: Use the semantic `::` format for rules to enable Anki export.
    - **Vocab Pages**: Use the semantic `::` format for all entries.
    - Create new pages if the topic is novel.
4. **Index**: Add/update entries in `wiki/index.md`.

### ❓ Query Flow
When asked about a word or rule:
1. Search the `/wiki/` folder first.
2. Provide the answer with a link to the specific wiki page.

### 🧹 Lint Flow (Periodic)
- Identify "Orphan" vocabulary.
- Suggest review topics based on the `log.md`.
- **Tense Audit**: Identify which grammar pages haven't been "recapitulated" recently.

## Formatting Conventions
- **Links**: MUST use double brackets: `[[Page Name]]`.
- **Source Links**: Every example must be linked to its source: `"Sentence" [[Source File]]`.
- **Anki Semantic Style**: Use the double colon `::` to separate the Front (Spanish) from the Back (German/Explanation).
- **Vocabulary Entries**: `Spanish Word (Gender) :: German Translation [Level] ["Sentence" [[Source File]]]`
- **Grammar Entries**: `Grammar Point/Question :: German Explanation [Example] [[Source File]]`
