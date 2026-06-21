# AGENTS.md

## Project

IAproject is a Spring Boot and Angular app for generating study questions about computer science and software development topics.

Keep the MVP focused on this learner flow:

1. Browse topics and skills.
2. Select topic, difficulty, and question type.
3. Generate a study question.
4. Show answer and explanation.
5. Keep agents/tools visible in the UI and API.

Question generation is currently template-based. Do not add an external AI provider until the local flow is stable.

## Language

- Code, comments, docs, commits, branches, UI text, API names, classes, and files: English.
- Conversation with the project owner: Spanish is allowed.

## Stack

- Backend: Java 21, Spring Boot, Maven Wrapper, H2 for development.
- Frontend: Angular, TypeScript, CSS.
- Future database target: PostgreSQL.

## Work Style

- Prefer targeted searches and focused file reads over scanning the whole repository.
- Do not refactor, rename, or reformat unrelated code without permission.
- Keep changes small, explicit, and aligned with the current structure.
- Apply Clean Code and SOLID when they improve clarity.
- Do not expose secrets, tokens, credentials, stack traces, or internal details.

## Backend Rules

Use hexagonal architecture:

```text
backend/src/main/java/com/iaproject/backend/
  domain/
  application/
  infrastructure/
  api/
```

- `domain` must not depend on Spring, JPA, HTTP, databases, or external APIs.
- `application` orchestrates use cases through ports.
- `infrastructure` implements adapters for persistence, AI providers, tools, and external services.
- `api` contains thin REST controllers and HTTP DTOs.
- Validate incoming requests before executing use cases.
- Keep question generation behind a port.

## Product Terms

- Agents: study task components, such as `QuestionGeneratorAgent`, `AnswerReviewerAgent`, and `StudyPlannerAgent`.
- Skills: topic-specific capabilities or knowledge areas.
- Tools: reusable actions, such as `GenerateQuestionTool`, `EvaluateAnswerTool`, and `SuggestNextTopicTool`.
- Topics, questions, and future quizzes are core domain concepts.

## Frontend Rules

- Build the usable study app as the first screen, not a marketing page.
- Use clear controls: selects, buttons, cards, badges, compact sections.
- Keep layouts responsive.
- Validate input before API calls.
- Handle loading, empty, and error states.

## Security

- Validate all external input.
- Use safe CORS defaults and only allow required origins.
- Do not hardcode or log secrets, tokens, passwords, credentials, or personal data.
- Return safe error responses without stack traces.
- Add authentication and authorization before storing user-specific progress.
- Use environment variables for environment-specific configuration.

## Commands

```powershell
cd backend
.\mvnw.cmd test
.\mvnw.cmd spring-boot:run
```

```powershell
cd frontend
npm install
npm start
npm run build
npm test -- --watch=false
```

## Verification

- Run the smallest relevant test first.
- Before finishing code changes, run relevant backend and/or frontend checks when practical.
- If a check cannot be run, state why.

## Codex Skills

- Keep project-specific skills under `.codex/skills/`.
- Use `.codex/skills/learning-log-updater` as the canonical skill for `AI_LEARNING_LOG.md`.
- Do not copy global personal skills into this repository.

## Git

- Do not commit or push unless the project owner asks.
- Do not revert user changes unless explicitly requested.
- Keep commits focused and written in English.
