# How this repository was made (Uruguaiana)

This file is written by the build on 2026-11-06, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Câmara Municipal de Uruguaiana, SAPL: records of the municipal laws and their PDFs (newest first) | <https://sapl.uruguaiana.rs.leg.br/norma/pesquisar> | 2026-11-02 | Texts: Câmara Municipal de Uruguaiana, SAPL (Sistema de Apoio ao Processo Legislativo), sapl.uruguaiana.rs.leg.br; SAPL: "Conteúdo e dados sob licença Creative Commons 4.0 Atribuir Fonte - Compartilhar Igual". Lei 9.610/1998 art. 8 IV: the texts of laws and other official acts are not protected by copyright. Non-official text: only the official gazette is authoritative. |
| Câmara Municipal de Uruguaiana, SAPL: records of the municipal laws and their PDFs (newest first) | <https://sapl.uruguaiana.rs.leg.br/norma/pesquisar> | 2026-11-06 | Texts: Câmara Municipal de Uruguaiana, SAPL (Sistema de Apoio ao Processo Legislativo), sapl.uruguaiana.rs.leg.br; SAPL: "Conteúdo e dados sob licença Creative Commons 4.0 Atribuir Fonte - Compartilhar Igual". Lei 9.610/1998 art. 8 IV: the texts of laws and other official acts are not protected by copyright. Non-official text: only the official gazette is authoritative. |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `lei-2024-05777` | Lei nº 5.777, de 18 de setembro de 2024 | 1 | 2024-09-19 to 2024-09-19 |
| `lei-2019-05080` | Lei nº 5.080, de 11 de outubro de 2019 | 1 | 2019-10-15 to 2019-10-15 |
| `lei-2019-05079` | Lei nº 5.079, de 11 de outubro de 2019 | 1 | 2019-10-15 to 2019-10-15 |
| `lei-2019-05077` | Lei nº 5.077, de 8 de outubro de 2019 | 1 | 2019-10-09 to 2019-10-09 |
| `lei-2019-05076` | Lei nº 5.076, de 8 de outubro de 2019 | 1 | 2019-10-09 to 2019-10-09 |
| `lei-2019-05075` | Lei nº 5.075, de 8 de outubro de 2019 | 1 | 2019-10-09 to 2019-10-09 |
| `lei-2019-05074` | Lei nº 5.074, de 30 de setembro de 2019 | 1 | 2019-10-01 to 2019-10-01 |
| `lei-2019-05073` | Lei nº 5.073, de 23 de setembro de 2019 | 1 | 2019-09-24 to 2019-09-24 |
| `lei-2019-05071` | Lei nº 5.071, de 23 de setembro de 2019 | 1 | 2019-09-24 to 2019-09-24 |
| `lc-2019-00025` | Lei Complementar nº 25, de 12 de setembro de 2019 | 1 | 2019-09-13 to 2019-09-13 |

The build made 10 commits:

| Commits | Kind |
| ---: | --- |
| 10 | first version of an act |
| 0 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `futuro`: laws not yet in force on 2026-11-06.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 10 laws in the record.
- 20 tags.

## Dates

Each commit is dated at noon (America/Sao_Paulo) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: Decreto-Lei 4.657/1942 (LINDB) art. 1: unless it says otherwise, a law takes effect 45 days after its official publication. This record takes in only municipal laws whose own vigência clause says they take effect on their publication (or signature), and dates each by the publication date the Câmara's SAPL records for it (else by its date). https://www.planalto.gov.br/ccivil_03/decreto-lei/del4657compilado.htm

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `aba32daaf554bb3da36fc460a85c73719b1ec10e51ee355b73e2c0e67796cb88` (88413 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `35388bee5aa05369f7da68f5a8fa015ea8d442b8`, `check.py` `5d719354ea4c62d240c93d2cae446307d81d9e81`, `on.py` `aff48cf1b68d50c7ba8f399ca32261871c301824`.
- Python 3.14.4; git version 2.53.0.

## Checks

Not yet run for this build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- Each municipal law ("Lei" and "Lei Complementar") is given as enacted, from the PDF the Câmara's SAPL holds for it, credited to the law itself and dated by the publication date SAPL records for it (else by the law's own date). Later amendments by other laws are not worked into earlier laws: each law is its own file set as enacted. Laws are taken newest first, in parts.
- Left out: scans (with or without an OCR layer), PDFs whose heading does not carry the record's number, texts with no article or no closing date line, texts carrying alteration notes, and laws whose vigência clause sets another day than their publication (or that have none, so that the 45 days of the LINDB apply).
- The text runs from the law's heading to its closing date line (signatures after it are left out); lines repeated at the top or bottom of two or more pages (letterheads, footers) and page numbers are left out. Lines are joined into paragraphs: a new paragraph starts at a provision label, a heading line, or after a line ending in ".", ";" or ":". One file per Art.; "000-titulo" holds what comes before the first article.
- Each municipal law ("Lei" and "Lei Complementar") is given as enacted, from the PDF the Câmara's SAPL holds for it, credited to the law itself and dated by the publication date SAPL records for it (else by the law's own date). Later amendments by other laws are not worked into earlier laws: each law is its own file set as enacted. Laws are taken newest first, in parts.
- Left out: scans (with or without an OCR layer), PDFs whose heading does not carry the record's number, texts with no article or no closing date line, texts carrying alteration notes, and laws whose vigência clause sets another day than their publication (or that have none, so that the 45 days of the LINDB apply).
- The text runs from the law's heading to its closing date line (signatures after it are left out); lines repeated at the top or bottom of two or more pages (letterheads, footers) and page numbers are left out. Lines are joined into paragraphs: a new paragraph starts at a provision label, a heading line, or after a line ending in ".", ";" or ":". One file per Art.; "000-titulo" holds what comes before the first article.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- Claude Code (claude-opus-5-5) wrote Lexifina's code and chose the sources. No model output is used as legal text or dates: every word comes from the Câmara's SAPL.
- Claude Code (claude-opus-5-5) wrote Lexifina's code and chose the sources. No model output is used as legal text or dates: every word comes from the Câmara's SAPL.
