# 🏢 DevTeam AI V3.0 Essential - Local-First Software House

> Sistema multiagente de 13 especialistas otimizado para desenvolvimento de software local de alta qualidade.

## 📋 Visão Geral (V3.0)

O **DevTeam AI V3.0** foi reescrito para eliminar a complexidade de nuvem e focar no que importa: **Qualidade de Código (`Software Craftsmanship`)** e **Velocidade de Execução Local**.

### Principais Mudanças
1.  **Zero Cloud Overhead**: Removidos agentes de Docker/K8s/CI complexos. Foco em construir o app na sua máquina.
2.  **13 Especialistas**: Papéis granulares (Product Manager, Scrum Master, UI/UX, Security, QA...) para cobrir todo o SDLC.
3.  **Slash Commands**: Controle total do pipeline com comandos como `/product`, `/code`, `/test`.
4.  **Glass Box Observability**: Raciocínio visível através da ferramenta `Sequential Thinking`.

---

## 👥 O Time (13 Especialistas)

| Domínio | Agente | Comando | Função Principal |
|:---|:---|:---|:---|
| **Product** | Product Manager | `/product` | Define a Visão e Backlog do Produto. |
| **Product** | Business Analyst | `/analysis` | Detalha requisitos em User Stories. |
| **Product** | System Analyst | `/systems` | Especifica contratos de API e Dados. |
| **Process** | Scrum Master | `/scrum` | Planeja a Sprint e remove bloqueios. |
| **Process** | Tech Writer | `/docs` | Documentação técnica e de usuário. |
| **Process** | Support Engineer | `/support` | Simulação de uso e Feedback loop. |
| **Design** | UI/UX Designer | `/uiux` | Cria Design System e Mockups. |
| **Engineering** | Architect | `/architecture` | Desenha a estrutura e stack tecnológica. |
| **Engineering** | Tech Lead | `/tech-plan` | Plano de implementação técnica. |
| **Engineering** | Senior Developer | `/code` | Implementação (Clean Code + TDD). |
| **Quality** | Security Engineer | `/security-design` | Modelagem de ameaças (Pre-Code). |
| **Quality** | QA Engineer | `/test` | Testes automatizados e manuais. |
| **Quality** | Security Validation | `/security-validation` | Validação de segurança (SAST/DAST). |


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
project-root/
├── .agent/
│   ├── workflows/               # Atalhos dos Slash Commands
│   ├── memory/                  # Project Context & Lessons Learned
│   └── project_state.json       # Estado atual do pipeline
├── orchestrator/                # Agente Coordenador
├── specialists/                 # Os 13 Agentes (01 a 13)
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
