---
name: task-follow-up
description: This skill should be used when the user asks about or changes their own work in Bufete, such as "what's on my plate", "mis tareas de hoy", "what is overdue", "create a task to", "add follow-ups from this meeting", "turn these notes into tasks", "mark the task as done" or "move the deadline". It reads the user's tasks and creates or updates them in Bufete after the user confirms.
---

# Task follow-up with Bufete

Help the user keep their own Bufete tasks current. The tools act only on tasks assigned to the signed-in lawyer.

## Show the work

1. Call `find_my_tasks`. Use the filters that fit the request: `overdue` for late work, `status`, `priority`, `matterId` for one matter, `search` for text.
2. The tool returns up to 25 tasks, soonest due first, and the total. When the total is larger, say so and narrow the filters.
3. Group the answer by due date: overdue, today, this week, later, no due date. Give each task its matter and priority.

## Create tasks

1. Read the source the user gives: notes, an email, a meeting summary, a document. Draft the list of tasks first. Each task gets a short title that starts with a verb, a due date when the source gives one, a priority and the matter it belongs to.
2. Find the matter id with `list_matters` when the user names a case or a client.
3. Show the list and wait for the user to confirm or change it. Do not create tasks before the user confirms.
4. Call `create_task` once per confirmed task. A second call creates a second task, so never repeat a call for a task already created.
5. Report what was created, with titles and due dates.

## Update tasks

1. Find the task with `find_my_tasks` and confirm it is the right one when more than one matches.
2. Call `update_task` with the task id and only the fields that change. Status `done` completes the task. A `dueDate` of null removes the due date.
3. Report the change.

## Rules

- Dates go in `YYYY-MM-DD` form. Turn relative dates such as "next Friday" into a date and show it to the user before saving.
- Tasks are assigned to the signed-in lawyer. To give work to a colleague, tell the user to assign it in Bufete.
- Write in the user's language.
