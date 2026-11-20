---
name: matter-brief
description: This skill should be used when the user asks for the status or a summary of one of their firm's cases or projects, such as "brief me on the Pérez case", "dame un resumen del caso", "where are we on this matter", "prepare me for the hearing", "what happened in court on this case" or "what is pending on this client's matter". It builds a brief from the matter's record, court cases, documents and tasks in Bufete.
---

# Matter brief with Bufete

Build a brief of one matter from the firm's records in Bufete. Use only what the tools return.

## Find the matter

1. Call `list_matters` with a short text from the matter name or the client name.
2. When more than one matter matches, show the candidates with their client and status and ask which one. When none matches, ask for another name.

## Read the record

1. Call `get_matter` with the matter id. It returns the client, the parties, the team, the responsible attorney, the background, the outcomes, and the court cases the matter follows with their next hearings, latest docket entries, decisions and court updates that nobody has attended to.
2. Call `search_documents` with the `matterId` and no query to list the matter's documents, most recently changed first. When the user asks about a topic, add a `query`.
3. Read the documents that matter for the brief with `read_document`: the latest filings, the contract in dispute, the last ruling. Read only the parts needed. A document whose `processingStatus` is not `READY` has no text yet: name it and move on.
4. Call `find_my_tasks` with the `matterId` to get the user's open tasks on the matter.

## Write the brief

Write in the user's language. Keep it short enough to read before a meeting. Use this order:

1. **Matter.** Name, client, kind, status, responsible attorney.
2. **Where it stands.** Three to five sentences on the current position.
3. **Court.** Each court case with its next hearing, its latest docket entries and decisions with dates. Put court updates that nobody has attended to first.
4. **Key documents.** The documents read, each with one line on what it says that matters now.
5. **Open tasks.** The user's tasks on the matter with due dates. Mark overdue tasks.
6. **Gaps and risks.** Missing documents, deadlines without a task, facts the record does not show.
7. **Suggested next steps.**

Give dates as the record gives them. Do not invent facts, deadlines or parties. When the record does not show something, say so.

## Follow-up

Offer to create tasks for the next steps. Create them only after the user confirms the list, with `create_task` and the `matterId`. The `task-follow-up` skill covers task work.
