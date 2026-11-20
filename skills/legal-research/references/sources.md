# Bufete research sources

## Law library (`search_law_library`, `read_law_library`)

| Collection | Content | Unit of a result |
|---|---|---|
| Dominican Republic | The Bufete legal wiki of Dominican laws, codes and decrees, with the recorded standing of each norm | A passage of the law it names |
| Colombia | National norms from SUIN-Juriscol, stored article by article with their vigencia notes | An article with its annotations |
| Mexico, federal | Federal laws published by the Cámara de Diputados | A passage of the law text, with a label that names the article where it starts |
| Mexico, states | Constitutions, codes and laws of the 31 states and Mexico City, from the Suprema Corte legislation system | A passage, as for federal law |
| United States | Federal and state law | A section passage |
| Global | International and comparative legal texts of the Bufete legal wiki | A passage of the text it names |

- A search with no jurisdiction searches the jurisdictions of the user's firm.
- A search of Mexico with no state covers federal law. Name the state to search its law.
- The in-force annotations of Colombian articles come from SUIN. They are informative, not certified. Give the source and the check date.

## Court rulings (`search_case_law`, `read_case_law`)

| Court or database | Jurisdiction |
|---|---|
| Juristeca | Dominican Republic |
| Corte Constitucional de Colombia | Colombia |
| Corte Suprema de Justicia de Colombia | Colombia |

- Rulings are read live from each court's own database. A court that is down shows in `unavailableSources`.
- Each source matches terms its own way. Short queries with distinctive terms work best.

## Dominican bills (`search_legislation`, `read_legislation`)

Bills of the Senate and the Chamber of Deputies, from introduction to promulgation, with their legislative history and attached documents. Sort by relevance, by relevance with recent bills first, by latest action or by introduction date. Filter by status, chamber, committee, practice area, bill type, sponsor and dates.

## Firm documents

`search_documents` and `read_document` reach the firm's own documents. Use them when the user asks about a contract, a filing or a memo of the firm, not for public law.
