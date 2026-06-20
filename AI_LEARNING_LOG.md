# AI Learning Log

This file tracks AI-assisted development concepts learned while building IAproject.

## 2026-06-20 - Project Setup, Agents, GitHub, and Skills

### Concepts Learned

- Project initialization: introduced how to start a new repository from an empty folder and create the first project documentation.
- README documentation: introduced how a README explains the project idea, goals, planned features, technologies, and next steps.
- Git basics: introduced local repository initialization, staging files, creating commits, configuring a remote, and pushing to GitHub.
- GitHub token usage: introduced how a token can authenticate repository creation and push operations without storing it in the remote URL.
- Spring Boot and Angular project structure: introduced a full-stack layout with `backend/` for the REST API and `frontend/` for the Angular app.
- Agents: introduced the idea of delegating a focused task to an agent, such as architecture planning or refactor review.
- Product agents: introduced agents as part of IAproject's domain, such as `QuestionGeneratorAgent`, `AnswerReviewerAgent`, and `StudyPlannerAgent`.
- Skills: introduced Codex skills as reusable instructions that guide future work.
- Tools: introduced tools as actions used by agents, such as `GenerateQuestionTool`, `EvaluateAnswerTool`, and `SuggestNextTopicTool`.
- Hexagonal architecture: introduced separating backend code into `domain`, `application`, `infrastructure`, and `api` layers.
- Clean Code and SOLID: introduced the importance of clear names, small responsibilities, framework-independent domain code, and maintainable boundaries.
- Security basics: introduced safe handling of tokens, request validation, CORS configuration, and safe error responses.

### Practical Actions

- Created an English `README.md` describing IAproject as a study-question generation web app.
- Created a public GitHub repository and pushed the initial README.
- Generated a Spring Boot backend and an Angular frontend.
- Built a first MVP screen for selecting a topic, difficulty, and question type.
- Added API endpoints for topics, skills, agents, tools, and question generation.
- Created `AGENTS.md` with project rules for architecture, security, Clean Code, SOLID, and language usage.
- Refactored the backend toward hexagonal architecture while preserving the existing API contract.
- Created the `learning-log-updater` skill to maintain this learning log.

### Key Vocabulary

- Repository: a Git project that stores source code and history.
- Commit: a saved snapshot of project changes.
- Remote: the GitHub repository connected to the local repository.
- Token: a secret credential used to authenticate with a service such as GitHub.
- Agent: an AI-assisted worker or product component that performs a focused task.
- Skill: reusable instructions that tell Codex how to handle a specific workflow.
- Tool: an executable action or capability used by an agent.
- Hexagonal architecture: an architecture style that keeps business logic independent from frameworks and infrastructure.
- Port: an interface that defines what the application needs from the outside world.
- Adapter: an implementation that connects a port to a concrete technology or data source.
- API contract: the request and response shape that frontend and backend agree to use.
- CORS: browser security rules that control which frontend origins can call the backend.

### Next Concepts To Learn

- Persist generated questions with a database adapter.
- Add quizzes and answer evaluation.
- Add authentication and authorization safely.
- Connect a real AI provider behind the current question generation port.
- Split the Angular UI into smaller pages and reusable components.
