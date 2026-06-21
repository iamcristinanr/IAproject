---
name: learning-log-updater
description: Update IAproject's AI learning log with concise milestone entries about what the project owner learns while building this project. Use when the user explicitly asks to use this skill, update AI_LEARNING_LOG.md, record what they learned, summarize concepts from the current conversation, or add a milestone about agents, skills, tools, GitHub, Spring Boot, Angular, architecture, security, or AI-assisted development in IAproject.
---

# Learning Log Updater

## Purpose

Maintain IAproject's learning log with what the project owner learns during development milestones.

Use this skill only when the user asks to update or use the learning log. Do not update the log automatically at the end of every task.

## Target File

Default to `AI_LEARNING_LOG.md` in the IAproject root.

If the file does not exist, create it with the structure in `references/log-format.md`.

## Workflow

1. Read the current conversation context and identify the concepts the user learned.
2. Read `AI_LEARNING_LOG.md` if it exists.
3. Add a new milestone entry instead of rewriting older entries.
4. Keep entries concise, practical, and written in English.
5. Include project-specific examples when useful.
6. Avoid exposing secrets, tokens, or private credentials.
7. Do not invent learning outcomes. If uncertain, phrase them as "Introduced" rather than "Mastered".

## Entry Content

Each milestone should include:

- Date.
- Short title.
- Concepts learned.
- Practical actions completed.
- Key vocabulary.
- Next concepts to learn.

## Style

- Write the log in English.
- Keep explanations beginner-friendly but technically accurate.
- Prefer bullets over long paragraphs.
- Use concrete examples from the project.
- Keep code or command snippets short.

## Safety

- Never include GitHub tokens, API keys, passwords, or full secrets.
- Mention that a token was used only in general terms.
- Do not include personal data unless the user explicitly asks for it.
