---
description: Pipeline de desenvolvimento otimizado com Estratégia de Produto e Agentes Especializados (v3.0 Essential)
---

# 🔄 Workflow: Pipeline de Desenvolvimento Local (v3.0 Essential)

Este workflow define o ciclo de vida de desenvolvimento V3.0, focado em alta eficiência local e qualidade de software ("Software Craftsmanship"). A infraestrutura de nuvem foi removida em favor de containers locais e robustez de código.

## 🌟 Visão Geral do Pipeline (14 Passos)

1.  **Product Manager (`/product`)**: Visão, Backlog e Priorização.
2.  **Scrum Master (`/scrum`)**: Planejamento da Sprint e Remoção de Impedimentos.
3.  **Business Analyst (`/analysis`)**: Detalhamento funcional (User Stories).
4.  **System Analyst (`/systems`)**: Especificação técnica (API/Dados).
5.  **Software Architect (`/architecture`)**: Design do sistema e Stack.
6.  **UI/UX Designer (`/uiux`)**: Design System e Prototipagem.
7.  **Security Design (`/security-design`)**: Modelagem de Ameaças (Pre-Code).
8.  **Tech Lead (`/tech-plan`)**: Quebra de tarefas técnicas e Code Guidelines.
9.  **Senior Developer (`/code`)**: Implementação (Clean Code + TDD).
10. **DBA (`/database`)**: Schemas, Migrations e Performance de Dados.
11. **QA Engineer (`/test`)**: Testes E2E, Regressão e Quality Gate.
12. **Security Validation (`/security-validation`)**: Validação de implementação (SAST/DAST).
13. **Technical Writer (`/docs`)**: Documentação Técnica e de Usuário.
14. **Support Engineer (`/support`)**: Simulação de Suporte e Feedback Loop.

---

## 🚀 Execução Detalhada

### 💡 Passo 1: Product Manager
**Comando:** `/product`
**Agente:** `product/product_manager.md`
**Output:** `product_backlog.md`
**Ação:** Define "O QUE" construir e "POR QUE".

### 🔄 Passo 2: Scrum Master
**Comando:** `/scrum`
**Agente:** `process/scrum_master.md`
**Output:** `sprint_plan.md`
**Ação:** Define "O QUE CABE" na Sprint.

### 📋 Passo 3: Business Analyst
**Comando:** `/analysis`
**Agente:** `product/business_analyst.md`
**Output:** `detailed_specifications.md`
**Ação:** Detalha os critérios de aceite.

### 📝 Passo 4: System Analyst
**Comando:** `/systems`
**Agente:** `product/system_analyst.md`
**Output:** `technical_specifications.md`
**Ação:** Define contratos de API e modelos lógicos.

### 🏗️ Passo 5: Software Architect
**Comando:** `/architecture`
**Agente:** `engineering/software_architect.md`
**Output:** `architecture_design.md`
**Ação:** Define a estrutura do sistema.

### 🎨 Passo 6: UI/UX Designer
**Comando:** `/uiux`
**Agente:** `design/uiux_designer.md`
**Output:** `ui_design_system.md`
**Ação:** Define a aparência e fluxo visual.

### 🛡️ Passo 7: Security Engineer (Design)
**Comando:** `/security-design`
**Agente:** `quality/security_engineer.md`
**Output:** `security_policies.md`
**Ação:** Garante "Security by Design".

### 👨‍💻 Passo 8: Tech Lead
**Comando:** `/tech-plan`
**Agente:** `engineering/tech_lead.md`
**Output:** `implementation_plan.md`
**Ação:** Traduz arquitetura em tarefas para o dev.

### 💻 Passo 9: Senior Developer
**Comando:** `/code`
**Agente:** `engineering/senior_developer.md`
**Output:** Código Fonte (`src/`)
**Ação:** Escreve o software.

### 💾 Passo 10: DBA / Data Engineer
**Comando:** `/database`
**Agente:** `engineering/dba_data_engineer.md`
**Output:** Migrations e SQL Scripts.
**Ação:** Garante persistência e integridade.

### 🧪 Passo 11: QA Engineer
**Comando:** `/test`
**Agente:** `quality/qa_engineer.md`
**Output:** `test_report.md`
**Ação:** Valida funcionalidade e bugs.

### 🕵️‍♂️ Passo 12: Security Validation
**Comando:** `/security-validation`
**Agente:** `quality/security_validation_engineer.md`
**Output:** `security_validation_report.md`
**Ação:** Valida vulnerabilidades no código final.

### 📚 Passo 13: Technical Writer
**Comando:** `/docs`
**Agente:** `process/technical_writer.md`
**Output:** Documentação (`docs/`, `README.md`)
**Ação:** Documenta para o usuário e devs.

### 🎧 Passo 14: Support Engineer
**Comando:** `/support`
**Agente:** `process/support_engineer.md`
**Output:** `user_feedback_report.md`
**Ação:** Fecha o ciclo com insights de uso.

---

## 📂 Estrutura de Arquivos Final (V3.0)

```
project-root/
├── .agent/               # Configs e memórias dos agentes
├── src/                  # Código fonte (Senior Dev)
├── tests/                # Testes (QA)
├── docs/                 # Documentação (Tech Writer)
│   ├── adr/              # Decisões Arquiteturais
│   ├── api/              # Specs de API
│   └── guides/           # Manuais
├── database/             # Migrations e Seeds (DBA)
├── artifacts/            # Saídas dos Agentes (Histórico)
│   ├── 01_backlog.md
│   ├── 02_sprint_plan.md
│   ├── 03_specs.md
│   ├── 07_security_policies.md
│   ├── 08_tech_plan.md
│   └── 14_feedback.md
└── README.md             # Ponto de entrada
```

---
*DevTeam AI - Pipeline v3.0 Essential - Optimized for Local Development*
