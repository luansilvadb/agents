---
description: Propor uma nova mudança com o time de Planejamento (Fase 1-7)
---

# 🚀 /team:propose [descrição]

Aciona o time de especialistas para gerar a proposta completa, specs, design e políticas de segurança para uma nova mudança ou funcionalidade.

## 👥 Time de Planejamento
- **Product Manager**: Visão e Backlog (01)
- **Scrum Master**: Planejamento e Sprint (02)
- **Business Analyst**: Detalhamento Funcional (03)
- **System Analyst**: Especificação Técnica (04)
- **Software Architect**: Design Arquitetural (05)
- **UI/UX Designer**: Design System e Interface (06)
- **Security Engineer**: Modelagem de Ameaças (07)
- **Tech Lead**: Planejamento Técnico e Tasks (08)

## 📋 Sequência de Execução

```bash
# 1. Product Manager (Visão e Épicos)
agent run specialists/product/product_manager.md

# 2. Scrum Master (Capacidade e DoD)
agent run specialists/process/scrum_master.md

# 3. Business Analyst (User Stories e BDD)
agent run specialists/product/business_analyst.md

# 4. System Analyst (API Specs e Modelagem)
agent run specialists/product/system_analyst.md

# 5. Software Architect (Arquitetura e ADRs)
agent run specialists/engineering/software_architect.md

# 6. UI/UX Designer (Design System e Layouts)
agent run specialists/design/uiux_designer.md

# 7. Security Design (Políticas de Segurança)
agent run specialists/quality/security_engineer.md

# 8. Tech Lead (Task Breakdown e Guidelines)
agent run specialists/engineering/tech_lead.md
```

## 📂 Consolidação da Proposta

Após a execução dos agentes, os artefatos são consolidados no diretório da mudança:

```powershell
# Exemplo de comando para consolidar (será executado pelo Orquestrador)
$change_id = "{{descrição}}"
$path = "devteam/changes/$change_id"
mkdir -p $path
mv artifacts/01_backlog.md $path/proposal.md
mv artifacts/03_specs.md $path/specs.md
mv artifacts/05_architecture.md $path/design.md
mv artifacts/08_tech_plan.md $path/tasks.md
```

**Output Esperado**:
- `devteam/changes/[id]/proposal.md` — why we're doing this, what's changing
- `devteam/changes/[id]/specs/` — requirements and scenarios (BDD)
- `devteam/changes/[id]/design.md` — technical approach (Architecture + Design System)
- `devteam/changes/[id]/tasks.md` — implementation checklist (Tasks < 8h)
