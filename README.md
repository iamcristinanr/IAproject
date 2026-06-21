# IAproject

IAproject is a Spring Boot and Angular web application designed to generate study questions for any topic related to computer science and software development.

The goal is to help students, developers, and interview candidates practice technical concepts through generated questions, explanations, and quizzes.

## Project Idea

The application will allow users to enter a topic and generate useful study questions about it.

Example topics include:

- Java
- Backend development
- Frontend development
- Spring Boot
- Cybersecurity
- Databases
- REST APIs
- Software architecture
- Git and GitHub
- Docker
- Testing

## Main Goal

Build a platform that helps users study technical subjects by creating questions adapted to the selected topic and difficulty level.

## Planned Features

- Generate questions from a topic entered by the user.
- Support different difficulty levels: beginner, intermediate, and advanced.
- Include answers or explanations to help users understand each concept.
- Organize questions by category, such as Java, backend, frontend, or security.
- Save questions for later review.
- Create practice quizzes or tests.
- Help users prepare for exams, interviews, certifications, or personal learning.

## Possible Technologies

The project may be built using technologies such as:

- Java
- Spring Boot
- HTML, CSS, and JavaScript
- React, Angular, or Vue
- REST APIs
- SQL or NoSQL databases
- Artificial intelligence services

## Project Status

This project is in its initial MVP phase. The repository now contains a Spring Boot REST API and an Angular frontend.

## Architecture

```text
IAproject/
  backend/    Spring Boot REST API
  frontend/   Angular single-page application
```

The MVP models agents, skills, and tools as first-class study concepts:

- `QuestionGeneratorAgent` creates questions for selected technical topics.
- `AnswerReviewerAgent` will evaluate answers and explain mistakes.
- `StudyPlannerAgent` will suggest what to study next.
- `GenerateQuestionTool`, `EvaluateAnswerTool`, and `SuggestNextTopicTool` represent reusable actions used by agents.

## Codex Skills

This repository can include project-local Codex skills when they support IAproject-specific workflows.

- `.codex/skills/learning-log-updater` updates `AI_LEARNING_LOG.md` with project learning milestones.

Personal or global Codex skills, such as Git/GitHub workflow helpers or technical documentation helpers, are not stored in this repository.

## API Endpoints

```http
GET  /api/topics
GET  /api/skills
GET  /api/agents
GET  /api/tools
POST /api/questions/generate
```

## Local Development

Run the backend:

```bash
cd backend
./mvnw spring-boot:run
```

On Windows PowerShell:

```powershell
cd backend
.\mvnw.cmd spring-boot:run
```

Run the frontend:

```bash
cd frontend
npm start
```

The frontend runs on:

```text
http://localhost:4200
```

The backend runs on:

```text
http://localhost:8080
```

## Next Steps

- Add persistent storage for generated questions and quizzes.
- Add quiz sessions and answer evaluation.
- Add authentication and user progress.
- Replace template-based generation with an AI provider behind the current agent/tool API.
- Add admin CRUD for topics, skills, agents, and tools.

## License

The license has not been defined yet.
