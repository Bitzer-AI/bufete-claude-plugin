---
name: legal-research
description: This skill should be used when the user asks a legal question that needs sources, such as "what does the law say about", "find the article on", "is this article in force", "find case law on", "busca jurisprudencia sobre", "qué dice la ley", "hay algún proyecto de ley sobre", or asks for a cited legal memo on Dominican, Colombian, Mexican or United States law. It researches enacted law, court rulings and Dominican bills through the Bufete tools and answers with citations to what was read.
---

# Legal research with Bufete

Answer legal questions from primary sources that the Bufete tools return. Cite only text that was read in this conversation.

## Before searching

1. Identify the jurisdiction, the legal issue and the facts that matter. When the jurisdiction is not clear from the question or the conversation, ask one short question.
2. Omit the jurisdiction filter when the user does not name one. The tools then search the jurisdictions of the user's firm.
3. Write search queries in the language of the law: Spanish for the Dominican Republic, Colombia and Mexico, English for the United States. Use the terms a statute or a ruling would use, not the user's paraphrase.

## Enacted law

1. Call `search_law_library` with a short query that names the legal concept. Run two or three focused searches with different terms instead of one long query.
2. Read each result to cite with `read_law_library`, passing its `sourceType` and `sourceId`. A search hit is a passage, not the full article.
3. Report the standing that the result carries. For an article with in-force annotations, give its status, the source of the annotation and the check date. When the status is not confirmed, say so. Never call an article in force when its annotations or its norm say otherwise.
4. A Mexican result is a passage of the law text with a label. It has no in-force status of its own: read the reform notes inside the text and report them.
5. `unavailableJurisdictions` lists collections that did not answer. Say that those collections could not be searched. Their silence does not mean that no law exists.

## Court rulings

1. Call `search_case_law` with a few distinctive terms in Spanish, one phrasing per search. For an exact phrase, send the whole query as one phrase inside double quotes.
2. Read a ruling with `read_case_law` before citing it. Continue with `nextChunk` when the part that matters is further in.
3. `unavailableSources` lists courts that did not answer. Say so in the answer. Their silence is not a sign that no precedent exists.
4. Report each ruling with its court, number or identifier, date and the holding that applies. Quote the short passage that supports the point.

## Dominican bills

1. Call `search_legislation` when the question is about a law in preparation, a reform under discussion or the legislative history of a norm.
2. Read a bill with `read_legislation`. Pass a query to get the passages of that bill that match.
3. State that a bill is not law until it is promulgated. Give its status and its latest legislative action with the date.

## Answer

Write the answer in the user's language. Use this order:

1. **Short answer.** Two to four sentences.
2. **Legal basis.** Each rule with its citation: the law and article, or the ruling. Add the in-force status for each article.
3. **Limits.** Sources that did not answer, statuses that are not confirmed, facts that change the answer.
4. **Next steps.** What the lawyer should check or do next.

Keep quotations short and exact. When the sources do not answer the question, say so and say what was searched. Do not fill gaps from memory: an answer from memory must be marked as such and checked against a source.

For the coverage of each collection and court, read `references/sources.md`.
