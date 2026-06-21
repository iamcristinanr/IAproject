# AGENTS.md

## Project Context

IAproject is a Spring Boot and Angular web application for generating study questions about computer science and software development topics.

The product should help users study topics such as Java, backend development, frontend development, Spring Boot, cybersecurity, databases, REST APIs, Docker, Git/GitHub, testing, and software architecture.

## Language Rules

- Code, comments, documentation, commits, branches, UI text, API names, classes, and files must be written in English.
- Conversation with the project owner can be in Spanish.

## Engineering Principles

- Use hexagonal architecture for the backend.
- Keep business logic independent from frameworks and infrastructure.
- Apply Clean Code principles: clear names, small methods, simple control flow, and minimal duplication.
- Apply SOLID principles where they improve clarity and maintainability.
- Prefer explicit, readable code over clever abstractions.
- Keep security in mind from the beginning, especially input validation, authentication, authorization, error handling, and secret management.
- Do not expose secrets, tokens, credentials, stack traces, or internal implementation details.

## Tech Stack

- Backend: Java 21, Spring Boot, Maven Wrapper.
- Frontend: Angular, TypeScript, CSS.
- Current development database: H2.
- Future database target: PostgreSQL.

## Repository Structure

```text
IAproject/
  backend/    Spring Boot REST API
  frontend/   Angular single-page application
  README.md
  AGENTS.md
```

## Backend Architecture

The backend should follow hexagonal architecture:

```text
backend/src/main/java/com/iaproject/backend/
  domain/          Core business model and domain rules
  application/     Use cases and ports
  infrastructure/  Adapters, persistence, external services, configuration
  api/             REST controllers and HTTP DTOs
```

Rules:

- Domain code must not depend on Spring, JPA, HTTP, databases, or external APIs.
- Application services orchestrate use cases through ports.
- Infrastructure implements adapters for persistence, AI providers, tools, and external systems.
- REST controllers should be thin and delegate to application services.
- Validate incoming requests before executing use cases.
- Keep generated question logic behind a port so template-based generation can later be replaced by an AI provider.

## Product Concepts

The project models these concepts as part of the application domain:

- Agents: components that perform study-related tasks.
- Skills: topic-specific capabilities or knowledge areas.
- Tools: reusable actions used by agents.
- Topics: study areas selected by the user.
- Questions: generated study questions.
- Quizzes: future practice sessions made from questions.

Current MVP examples:

- `QuestionGeneratorAgent`
- `AnswerReviewerAgent`
- `StudyPlannerAgent`
- `GenerateQuestionTool`
- `EvaluateAnswerTool`
- `SuggestNextTopicTool`

## Current MVP Scope

Focus on a working learner flow before adding advanced features:

1. Browse topics and skills.
2. Select a topic, difficulty, and question type.
3. Generate a study question.
4. Show the answer and explanation.
5. Keep the agent/tool model visible in the UI and API.

Question generation currently uses deterministic templates. Do not add an external AI provider until the local flow is stable.

## Security Guidelines

- Validate all external input.
- Use safe defaults for CORS and only allow required origins.
- Do not hardcode secrets in the repository.
- Do not log tokens, passwords, credentials, or personal data.
- Return safe error responses without internal stack traces.
- Add authentication and authorization before storing user-specific progress or private data.
- Prefer environment variables for configuration that differs by environment.

## Frontend Guidelines

- Build the usable app as the first screen.
- Keep the UI focused on studying, not marketing.
- Prefer clear controls: selects, buttons, cards, badges, and compact sections.
- Keep layouts responsive for desktop and mobile.
- Use English UI copy.
- Avoid decorative complexity that does not help the study workflow.
- Validate user input before sending requests.
- Handle loading, empty, and error states.

## Useful Commands

Backend:

```powershell
cd backend
.\mvnw.cmd test
.\mvnw.cmd spring-boot:run
```

Frontend:

```powershell
cd frontend
npm install
npm start
npm run build
npm test -- --watch=false
```

## Project Codex Skills

- Keep project-specific Codex skills under `.codex/skills/`.
- Use `.codex/skills/learning-log-updater` as the canonical skill for updating `AI_LEARNING_LOG.md`.
- The learning log records what the project owner learns about AI-assisted development while building IAproject.
- Do not treat the global `learning-log-updater` skill as the source of truth for this project if a local copy exists.
- Commit project-local skills only when they are part of IAproject's workflow and useful to future agents working in this repository.
- Do not copy or commit global personal skills into this repository. Global skills such as `git-github-practices` and `technical-docs-writer` should remain under the user's global Codex skills directory.

## Verification

Before finishing code changes, run the relevant checks:

```powershell
cd backend
.\mvnw.cmd test
```

```powershell
cd frontend
npm run build
npm test -- --watch=false
```

## Git Guidelines

- Do not commit or push unless the project owner asks for it.
- Do not revert user changes unless explicitly requested.
- Keep commits focused and written in English.

## Near-Term Roadmap

- Add persistence adapters for the current hexagonal backend.
- Add persistent storage for generated questions.
- Add quiz creation and quiz results.
- Add answer evaluation.
- Add topic detail pages.
- Add admin management for topics, skills, agents, and tools.
- Add authentication and user progress later.
- Add real AI integration behind the existing agent/tool abstraction.
