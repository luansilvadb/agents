# 🏗️ Project Context & Manifest (V3.1)

> **Source of Truth**: Dynamic registry of project state, constraints, and architecture.
> **Last Updated**: 2026-01-05
> **Maintainers**: Scrum Master, Architect, Tech Lead

---

## 1. System Metadata (YAML)
This block is the primary index for agent orientation.

```yaml
project_metadata:
  name: "[Project Name]"
  id: "proj-001-core" # Update with immutable ID
  version: "0.0.1-alpha"
  repository: "[Repo URL]"
  documentation_root: "docs"
  
project_config:
  language: "pt-BR"
  timezone: "America/Sao_Paulo (UTC-3)"
  agent_framework_version: "3.0.0"
```

## 2. Dynamic State (Pulse)
Current operational context. Update this section at Sprint boundaries.

```yaml
context_status:
  phase: "Planning" # Planning | Development | Stabilization | Release
  current_sprint: 0
  sprint_goal: "[Objetivo principal da iteração atual]"
  system_health: "Green" # Green | Yellow | Red
  active_blockers: 0
```

### 🎯 Key Deliverables (Sprint 0)
- [ ] [Deliverable 1]
- [ ] [Deliverable 2]

---

## 3. Architectural Blueprint
### 🛠️ Tech Stack (Core)
*See `memory/tech/` for detailed ADRs.*

```yaml
tech_stack:
  frontend: "[ex: React, Vite, Tailwind]"
  backend: "[ex: Node.js, Fastify]"
  database: "[ex: PostgreSQL, Prisma]"
  testing: "[ex: Vitest, Playwright]"
  infra: "[ex: Docker, AWS]"
```

### ⚖️ System Invariants (Non-negotiable)
All agents MUST validate actions against these Hard Constraints.

#### 🔐 Security & Ethics
1.  **Zero Secrets**: NUNCA commitar chaves ou segredos. Use `.env` e `1Password`.
2.  **Input Validation**: Strict validation (Zod/Joi) em todas as fronteiras de I/O.
3.  **Data Privacy**: Respeitar GDPR/LGPD. Não logar PII.

#### ⚡ Performance & Scale
1.  **SLA**: API Response < 200ms (P95).
2.  **Asset Optimization**: Imagens WebP/AVIF. Lazy load by default.
3.  **Code Complexity**: Cyclomatic complexity < 10.

#### 💻 Quality Standards
1.  **Language**: TypeScript (Strict Mode).
2.  **Style**: ESLint Standard + Prettier.
3.  **Testing**: Min 80% coverage em Business Logic.
4.  **Commits**: Conventional Commits (feat:, fix:, chore:).

---

## 4. Domain Context
### 📖 Ubiquitous Language (Glossary)
*Expand in `memory/domain/glossary.md`*

- **Usuário**: [Definição: Ator que interage com o sistema]
- **Cliente**: [Definição: Entidade que paga pelo serviço]
- **[Termo]**: [Definição]

---

## 5. Workspace Registry (Navigation)
Use this map to locate detailed information.

- **`memory/global/`**: Manifestos e regras globais.
- **`memory/episodic/`**: Contexto volátil (Sprints, Dailies).
- **`memory/semantic/`**: Conhecimento acumulado (Padrões, Tech, Domain).
- **`docs/`**: Documentação formal do usuário/sistema.
- **`src/`**: Código fonte da aplicação.
