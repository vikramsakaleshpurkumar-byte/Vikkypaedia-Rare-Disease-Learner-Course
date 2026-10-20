# Vikkypaedia Rare Disease Learner Course — LLM Wiki Schema (`AGENTS.md`)

This project implements the **LLM Wiki** architecture for **Vikkypaedia Rare Disease Learner Course**, built from *Nelson Pediatric Textbook of Rare Diseases: Genomic Etiologies and Genetic Diagnosis (1st Edition)*.

## Directory Architecture

1. **`raw/` (Immutable Source Layer)**
   - `raw/nelson_rare_diseases_1e.pdf` — Original 1,351-page textbook PDF.
   - `raw/Nelson_Rare_Diseases_Full_With_Figures.md` — Complete, single-file high-fidelity Markdown conversion with symbol-font CMap corrections and all raster + vector figures linked.
   - `raw/chapters/` — All 61 individual chapter Markdown files (`001_...md` to `061_...md`), `000_Front_Matter.md`, and `00_INDEX.md`.
   - `raw/chapters_raw/` — Per-chapter intermediate page-chunked extractions.

2. **`figures/` (Shared Visual Asset Layer)**
   - Contains all extracted raster figures (`fig_pXXXX_YY.jpg`) and rendered vector figures/pedigrees/pathways (`vfig_pXXXX_YY.jpg`) with clean, ASCII-safe filenames.

3. **`wiki/` (LLM-Owned Knowledge & Assessment Layer)**
   - `wiki/sections/Section_I.md` .. `Section_X.md` — Section-level synthesis tables, core pearls, and key genes across all 10 textbook sections.
   - `wiki/chapters/001_...md` .. `061_...md` — Enhanced chapter study guides with metadata headers, extracted OMIM/gene associations, high-yield clinical pearls, and full cleaned chapter text + tables + figures.
   - `wiki/flashcards/001_flashcards.md` .. `061_flashcards.md` — Active-recall flashcards per chapter (`<details>` click-to-reveal).
   - `wiki/mcqs/001_mcqs.md` .. `061_mcqs.md` — Board-style 4-option self-assessment MCQs with explanations.
   - `wiki/omim_gene_atlas.md` — Cross-chapter Rare Disease Gene & OMIM Catalog (`#xxxxxx` / `*xxxxxx`).

4. **`data/` & `Vikkypaedia_Rare_Disease_Course.html` (Interactive Offline Course Application)**
   - Static JavaScript bundles (`index_data.js`, `flashcards_data.js`, `mcqs_data.js`, `omim_atlas_data.js`, `chapters_bundle_1.js`, `chapters_bundle_2.js`) pre-loaded into `Vikkypaedia_Rare_Disease_Course.html` for instant zero-server offline execution over `file://`.

5. **`index.md` & `log.md`**
   - `index.md` — Master catalog with clickable `file:///C:/Users/India/Downloads/Vikkypaedia_Rare_Disease_Learner_Course/...` links.
   - `log.md` — Append-only chronological record of ingestions, builds, and audits.

## Maintenance Rules for Agents
- Never modify or delete `raw/nelson_rare_diseases_1e.pdf`.
- Always use clean, apostrophe-free, comma-free filenames in `figures/` (`fig_pXXXX_YY.jpg` / `vfig_pXXXX_YY.jpg`).
- Always use explicit `file:///C:/Users/India/Downloads/Vikkypaedia_Rare_Disease_Learner_Course/...` links for Markdown-to-Markdown navigation so links work in the IDE even when no workspace is open.
- Whenever updating `wiki/` pages, regenerate `index.md` and `data/*.js` bundles, append an entry to `log.md`, and run `verify_rare_course.py` to confirm 0 broken links.
