# 🏢 DevTeam AI V3.0 Essential - Local-First Software House

> Sistema multiagente de 14 especialistas otimizado para desenvolvimento de software local de alta qualidade.

## 📋 Visão Geral (V3.0)

O **DevTeam AI V3.0** foi reescrito para eliminar a complexidade de nuvem e focar no que importa: **Qualidade de Código (`Software Craftsmanship`)** e **Velocidade de Execução Local**.

### Principais Mudanças
1.  **Zero Cloud Overhead**: Removidos agentes de Docker/K8s/CI complexos. Foco em construir o app na sua máquina.
2.  **14 Especialistas**: Papéis granulares (Product Manager, Scrum Master, UI/UX, Security, QA...) para cobrir todo o SDLC.
3.  **Slash Commands**: Controle total do pipeline com comandos como `/product`, `/code`, `/test`.
4.  **Glass Box Observability**: Raciocínio visível através da ferramenta `Sequential Thinking`.

---

## 👥 O Time (14 Especialistas)

| ID | Agente | Comando | Função Principal |
|:---|:---|:---|:---|
| **01** | Product Manager | `/product` | Define a Visão e Backlog do Produto. |
| **02** | Scrum Master | `/scrum` | Planeja a Sprint e remove bloqueios. |
| **03** | Business Analyst | `/analysis` | Detalha requisitos em User Stories. |
| **04** | System Analyst | `/systems` | Especifica contratos de API e Dados. |
| **05** | Architect | `/architecture` | Desenha a estrutura e stack tecnológica. |
| **06** | UI/UX Designer | `/uiux` | Cria Design System e Mockups. |
| **07** | Security Engineer | `/security-design` | Modelagem de ameaças (Pre-Code). |
| **08** | Tech Lead | `/tech-plan` | Plano de implementação técnica. |
| **09** | Senior Developer | `/code` | Implementação (Clean Code + TDD). |
| **10** | DBA | `/database` | Banco de dados e Migrations. |
| **11** | QA Engineer | `/test` | Testes automatizados e manuais. |
| **12** | Security Validation | `/security-validation` | Validação de segurança (SAST/DAST). |
| **13** | Tech Writer | `/docs` | Documentação técnica e de usuário. |
| **14** | Support Engineer | `/support` | Simulação de uso e Feedback loop. |

---

## 🚀 Como Usar

### 1. Iniciar Projeto
Para começar um novo ciclo, simplesmente digite:

```bash
/start
```

Isso carregará o **Orquestrador**, que guiará você desde a definição do produto.

### 2. Navegação
Você não precisa decorar os comandos. O Orquestrador lhe dirá qual o próximo passo.
Mas se quiser pular direto para uma etapa:

- Quer mudar o backlog? Use `/product`.
- Quer escrever código? Use `/code`.
- Quer rodar testes? Use `/test`.

### 3. Acompanhamento
Para ver o status do projeto e os artefatos gerados:

```bash
/status
```

---

## 📁 Estrutura do Projeto

```
d:\agents\
├── .agent/
│   ├── workflows/               # Atalhos dos Slash Commands
│   ├── memory/                  # Project Context & Lessons Learned
│   └── project_state.json       # Estado atual do pipeline
├── orchestrator/                # Agente Coordenador
├── specialists/                 # Os 14 Agentes (01 a 14)
├── protocols/                   # Regras de Ética, Handoff e Memória
├── artifacts/                   # Saída dos Agentes (Docs, Plans)
└── src/                         # Código Fonte do seu Projeto
```

---

## 🏷️ Versionamento

- **Versão**: 3.0.0 Essential
- **Foco**: Local Development & Software Quality
- **Data**: 2026-01-05

---
*DevTeam AI - Transformando sua máquina em uma Software House.*
