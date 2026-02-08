---
# PHR: Create Project Constitution for The Evolution of Todo

**ID**: 1
**TITLE**: Create Project Constitution
**STAGE**: constitution
**DATE_ISO**: 2026-02-07
**SURFACE**: agent
**MODEL**: claude-sonnet-4-5-20250929
**FEATURE**: none
**BRANCH**: master
**USER**: AA

**COMMAND**: You are an expert constitution writer for spec-driven development using Spec-Kit Plus in a monorepo full-stack project...

**LABELS**: ["constitution", "spec-driven-development", "project-governance"]

**FILES_YAML**:
  - .specify/memory/constitution.md

**TESTS_YAML**:
  - None

**LINKS**:
  SPEC: null
  TICKET: null
  ADR: null
  PR: null

---

## PROMPT_TEXT

You are an expert constitution writer for spec-driven development using Spec-Kit Plus in a monorepo full-stack project.

Your role is to create the root-level constitution.md file that serves as the foundational governing document for the entire project. This file defines the project's principles, rules, conventions, workflows, and boundaries that all specs, CLAUDE.md files, agents, and implementations must follow.

The constitution must be comprehensive, clear, and aligned with the project's current phase and long-term vision.

Current project details (from the provided Phase II document):
- Project name: The Evolution of Todo - Phase II: Full-Stack Web Application
- Objective: Transform console app to multi-user web app with persistent storage using Claude Code + Spec-Kit Plus
- Tech stack:
  - Frontend: Next.js 16+ (App Router), TypeScript, Tailwind CSS
  - Backend: Python FastAPI, SQLModel (ORM)
  - Database: Neon Serverless PostgreSQL
  - Authentication: Better Auth with JWT
  - Development approach: Spec-Driven (Write spec → Plan → Tasks → Implement via Claude Code, no manual coding)
- Monorepo structure: hackathon-todo/ with .spec-kit/config.yaml, specs/ (overview, architecture, features/, api/, database/, ui/), CLAUDE.md (root + frontend/ + backend/), docker-compose.yml, frontend/, backend/
- API endpoints: /api/{user_id}/tasks (CRUD + toggle complete), all require JWT, user isolation enforced
- Future evolution: Phase III chatbot, intelligent agents/sub-agents/skills

Create the full content of **constitution.md** (root level) with this exact structure:

# Project Constitution - The Evolution of Todo

## 1. Project Vision & Purpose
- Long-term goal
- Current phase (Phase II) focus
- Success criteria

## 2. Core Principles
- Spec-driven development only
- No manual coding rule
- User isolation & security first
- Maintainability, scalability, testability
- Phase-based evolution

## 3. Development Workflow (Agentic Dev Stack)
- Step-by-step process: Write spec → Generate plan → Break into tasks → Implement via Claude Code
- How to use Spec-Kit Plus (@specs/ referencing)
- Role of CLAUDE.md files (root, frontend, backend)
- Iteration & review process

## 4. Technology & Tooling Rules
- Allowed tech stack (exact versions where possible)
- Forbidden patterns (e.g., no inline styles, no blocking calls in async)
- Environment variables (e.g., DATABASE_URL, BETTER_AUTH_SECRET)
- Docker Compose usage

## 5. Security & Compliance Rules
- JWT & Better Auth usage
- User isolation enforcement (backend filtering)
- No shared sessions
- Token handling best practices

## 6. Naming & Structure Conventions
- Folder & file naming
- Spec file structure (user stories, acceptance criteria, etc.)
- Component & route naming
- Database table/column naming

## 7. Testing & Quality Rules
- Integration testing requirements
- Coverage goals
- E2E vs unit vs integration

## 8. Phase Transition Rules
- When Phase II ends
- What must be complete before Phase III (chatbot/agents)
- Backward compatibility

## 9. Agent & Skills Guidelines
- How agents/sub-agents/skills must be designed
- Security & isolation for agent actions
- Future-proofing for chatbot phase

## 10. Governance
- How to update this constitution
- Version history

## RESPONSE_TEXT

Created the complete constitution.md file with all 10 sections as requested, covering project vision, core principles, development workflow, technology rules, security requirements, naming conventions, testing guidelines, phase transition rules, agent guidelines, and governance procedures. The constitution is tailored specifically to "The Evolution of Todo" project with Phase II requirements and future Phase III planning.

## OUTCOME

Successfully created the project constitution file with comprehensive governance for the spec-driven development approach using Claude Code and Spec-Kit Plus.

## EVALUATION

The constitution addresses all required aspects of the project governance, aligns with the Phase II objectives, and provides a solid foundation for future development phases. All specified sections were properly implemented with detailed guidance for the development team.
