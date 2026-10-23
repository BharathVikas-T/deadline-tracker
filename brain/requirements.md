# Deadline Tracker: Requirements

Part of [[index]]. Status: draft v1.

## Problem statement
Students forget deadlines and don't know what to start first. This app stores tasks with due dates and effort estimates. It ranks them so the student always knows the next task to work on.

## Scope
- A command-line app written in Python 3.11+
- Data stored locally in a SQLite database file
- Single user, no login

## Functional requirements (FR)
- **FR-1:** The user can add a task with title, subject, due date, estimated hours, and importance (1 to 3).
- **FR-2:** The app rejects a task if the title is empty, the hours are zero or negative, or the importance is not 1, 2, or 3.
- **FR-3:** The user can list all unfinished tasks. Overdue tasks appear first. All other tasks follow, ordered by priority score (highest first).
- **FR-4:** The user can mark a task as done, and it no longer appears in the unfinished list.
- **FR-5:** The app warns the user when the total estimated hours of unfinished tasks due within the next 48 hours exceeds 8 hours.
- **FR-6:** The user can filter the task list by subject.
- **FR-7:** The user can delete a task by its ID, and the app shows an error if the ID does not exist.
- **FR-8:** The user can edit any field of an existing task by its ID. The same validation rules as FR-2 apply, and the app shows an error if the ID does not exist.

## Non-functional requirements (NFR)
- **NFR-1:** Tasks must still be there after the app is closed and reopened.
- **NFR-2:** Listing tasks takes under 1 second for up to 1,000 tasks.
- **NFR-3:** Invalid input (wrong date format, text where a number is expected) produces a clear error message, not a crash.
- **NFR-4:** Core logic is covered by automated tests.

## Out of scope (for version 1)
- Web or mobile interface
- Reminders and notifications
- Repeating tasks
- Multiple users

## Assumptions (my decisions)
- Dates are entered as YYYY-MM-DD.
- Priority score is based on how soon a task is due and its importance. The exact formula is defined in the design stage.
- The 8-hour warning limit may change later.
- Decision: overdue tasks are always shown first; tasks can be edited after creation.

## Links
- Related: [[index]]