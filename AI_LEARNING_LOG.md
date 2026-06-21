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

## 2026-06-21 - Connecting Codex With GitHub and Notion Through MCP

### Concepts Learned

- MCP: introduced the Model Context Protocol as a way for Codex to connect with external tools through controlled, tool-specific integrations.
- GitHub integration: introduced how Codex can inspect repositories, issues, pull requests, files, commits, and project activity through a GitHub MCP connection.
- Notion integration: introduced how Codex can read and write shared Notion pages through a Notion MCP connection.
- Tool permissions: introduced the difference between read access, write access, and workspace-level limitations in external integrations.
- Documentation workflow: introduced Notion as a collaborative place for technical and functional project documentation while the source code remains in GitHub.
- Security awareness: reinforced that integrations should not expose tokens, credentials, secrets, or private implementation details in logs or documentation.

### Practical Actions

- Verified that Codex can access the configured Notion workspace through MCP using the `notion_codex` bot.
- Confirmed Notion write access by adding a short test paragraph to the shared `Codex` page.
- Learned that the Notion integration can write to pages shared with the integration, but cannot create private workspace-level pages directly from an internal integration.
- Connected the IAproject workflow with GitHub so Codex can help inspect repository state and support development tasks.
- Defined Notion as the place where Codex can help write and maintain technical documentation and functional documentation for IAproject.
- Recorded the Notion documentation page URL: https://app.notion.com/p/Codex-2a73bf6a0ee6805797e7f1bd3ce8c722

### Key Vocabulary

- MCP: a protocol that lets an AI assistant connect to external tools and data sources through explicit tool calls.
- GitHub MCP: an integration that lets Codex work with repository data such as files, branches, issues, pull requests, and commits.
- Notion MCP: an integration that lets Codex read, update, and create content in Notion pages that are available to the integration.
- Bot user: the Notion identity used by the integration to access shared pages.
- Technical documentation: documentation about architecture, setup, APIs, modules, data flow, deployment, and maintenance.
- Functional documentation: documentation about product behavior, user flows, features, business rules, and expected outcomes.
- Shared page: a Notion page explicitly made available to an integration so it can read or write content.

### Next Concepts To Learn

- Create a Notion documentation structure for IAproject, including technical and functional sections.
- Decide which documentation belongs in GitHub and which documentation belongs in Notion.
- Add templates for architecture notes, feature specifications, API documentation, and product decisions.
- Use GitHub issues or pull requests together with Notion documentation to keep implementation and planning aligned.

## 2026-06-21 - Codex Skills, Global Workflows, and Project-Local Automation

### Concepts Learned

- Codex skills: introduced skills as reusable instruction packages that teach Codex how to perform a recurring workflow with project-specific or domain-specific rules.
- Built-in Codex skills: introduced that Codex can provide system skills, such as skill creation, skill installation, OpenAI documentation lookup, image generation, and browser control.
- Custom global skills: introduced that personal reusable skills can live outside one project and be reused across workspaces, such as the technical documentation skill and the Git/GitHub practices skill.
- Project-local skills: introduced that IAproject can keep its own skills under `.codex/skills/` when they are tied to this repository, such as the learning log updater.
- Skill creation workflow: introduced the process of reading the `skill-creator` instructions, initializing a skill, writing `SKILL.md`, adding references, and validating the result.
- Git and GitHub best practices: introduced using short branch names, focused commits, Conventional Commit messages, PR summaries, verification notes, and safe Git behavior.
- Learning log automation: reinforced that the local `learning-log-updater` skill is the canonical workflow for updating `AI_LEARNING_LOG.md`.

### Practical Actions

- Reviewed official Git, GitHub, and Conventional Commits guidance before defining the Git/GitHub workflow.
- Created `git-github-practices` and moved it to the global skills directory so it can guide Git branches, commits, and pull requests across projects.
- Added examples for branch names, commit messages, pull request bodies, and weak commit messages to avoid.
- Validated the new Git/GitHub skill with the official skill validator.
- Kept `learning-log-updater` as a project-local skill because it updates IAproject's own `AI_LEARNING_LOG.md`.

### Key Vocabulary

- Built-in skill: a Codex-provided skill available for common workflows.
- Global skill: a reusable personal skill available across projects.
- Project-local skill: a skill stored inside a specific repository and tailored to that project's rules.
- Global skills directory: the user-level skills location, such as `C:\Users\usuario\.codex\skills`.
- `SKILL.md`: the required instruction file that defines a Codex skill.
- Frontmatter: the YAML metadata at the top of `SKILL.md`, including `name` and `description`.
- Reference file: an optional skill resource loaded when extra examples or detailed guidance are needed.
- Conventional Commit: a structured commit message such as `feat(frontend): add topic controls`.
- Pull request: a GitHub proposal to review and merge code changes.

### Next Concepts To Learn

- Decide which workflows should become global skills and which should stay project-local before committing them to a repository.
- Use the Git/GitHub practices skill when preparing real commits and pull requests.
- Improve the documentation skill with IAproject-specific templates if repeated documentation tasks appear.
- Learn how to version and evolve skills as the project workflow matures.
