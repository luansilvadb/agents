---
description: Pipeline de desenvolvimento otimizado com Estratégia de Produto e Agentes Especializados (v2.0)
---

# 🔄 Workflow: Pipeline de Desenvolvimento Integrado (v2.0)

Este workflow define o ciclo de vida completo de desenvolvimento de software utilizando a equipe DevTeam AI. Ele integra desde a concepção estratégica até a entrega e manutenção, seguindo as melhores práticas de Engenharia de Agentes 2025.

## 🌟 Visão Geral do Pipeline

1.  **Estratégia (Passo 0)**: Validação de ideia e modelo de negócio. (*Novo*)
2.  **Análise (Passo 1)**: Definição de requisitos de negócio.
3.  **Especificação (Passo 2)**: Tradução para requisitos técnicos.
4.  **Arquitetura (Passo 3)**: Design do sistema e decisões técnicas.
5.  **Implementação (Passo 4)**: Codificação assistida por IA.
6.  **Qualidade (Passo 5)**: Testes automatizados e QA.
7.  **Correção (Passo 6)**: Ciclos de debug e fix.
8.  **Otimização (Passo 7)**: Performance e refatoração.
9.  **Integração (Passo 8)**: DevOps e CI/CD.
10. **Documentação (Passo 9)**: Manuais e outputs finais.

---

## 🚦 Pré-requisitos
- Acesso à suite de agentes em `d:\agents\specialists\`
- Ferramentas de terminal configuradas (Node, Git, Docker)

---

## 🚀 Execução Detalhada

### 💡 Passo 0: Estratégia de Produto (PRODUCT STRATEGIST)
*Onde as ideias são validadas antes de gastar recursos.*

**Agente:** `specialists/00-product-strategist.md`
**Input:** Ideia bruta, insight de mercado ou problema.
**Output:** `strategic_blueprint.md` (Lean Canvas + Validação).

**Fluxo:**
1.  **Ideação**: Usuário apresenta a visão inicial.
2.  **Stress Test**: Agente desafia premissas e identifica riscos.
3.  **Modelagem**: Criação do Lean Canvas e Proposta de Valor Única (UVP).
4.  **Decisão Go/No-Go**: Validar se há "Product-Market Fit" teórico.

> 🛑 **Gate de Decisão**: Se a ideia não for viável, pivote AQUI. Não avance para o Passo 1.

---

### 📋 Passo 1: Análise de Negócios (ASK)
*Traduzindo visão em requisitos claros.*

**Agente:** `specialists/01-ask.md`
**Input:** `strategic_blueprint.md` (do Passo 0) + Entrevista com Cliente.
**Output:** `business_requirements.yaml`

**Fluxo:**
1.  Absorver o contexto estratégico do Blueprint.
2.  Conduzir entrevista detalhada para extrair requisitos funcionais.
3.  Priorizar features (MoSCoW) alinhadas ao valor de negócio.
4.  Gerar documento de requisitos de negócio.

---

### 📝 Passo 2: Especificação Técnica (SPECIFICATION WRITER)
*A ponte entre o negócio e a engenharia.*

**Agente:** `specialists/02-specification-writer.md`
**Input:** `business_requirements.yaml`
**Output:** `user_stories.yaml`, `non_functional_requirements.yaml` (NFRs).

**Fluxo:**
1.  Converter requisitos de negócio em User Stories técnicas.
2.  Definir critérios de aceite (Gherkin/BDD).
3.  Estipular Requisitos Não-Funcionais (Performance, Segurança).

---

### 🏗️ Passo 3: Arquitetura de Sistema (ARCHITECT)
*Fundação sólida para escala.*

**Agente:** `specialists/03-architect.md`
**Input:** User Stories + NFRs.
**Output:** `system_design.yaml`, `api_contracts.yaml`, `data_model.yaml`, `adrs/`

**Fluxo:**
1.  Selecionar stack tecnológica adequada aos NFRs.
2.  Desenhar diagrama de componentes e fluxos de dados.
3.  Definir contratos de API (OpenAPI/Swagger).
4.  Registrar Decisões Arquiteturais (ADRs).

---

### 💻 Passo 4: Implementação (AUTO-CODER)
*Construção do software.*

**Agente:** `specialists/04-auto-coder.md`
**Input:** Specs de Arquitetura e Especificação.
**Output:** Código Fonte (`src/`), `implementation_notes.md`.

**Fluxo:**
1.  Implementar scaffolding do projeto.
2.  Codificar features baseadas nas User Stories.
3.  Seguir estritamente os contratos de API e modelos de dados.
4.  Manter código limpo e comentado.

---

### 🧪 Passo 5: Testes e QA (TESTER)
*Garantia de qualidade.*

**Agente:** `specialists/05-tester.md`
**Input:** Código Fonte + Critérios de Aceite.
**Output:** `tests/` (Unit, E2E), `test_report.yaml`, `bug_report.yaml`.

**Fluxo:**
1.  Criar suíte de testes automatizados.
2.  Executar testes e registrar falhas.
3.  Validar critérios de aceite das User Stories.

---

### 🐛 Passo 6: Debugging & Fix (DEBUGGER / AUTO-CODER)
*Ciclo de correção.*

**Entrada:** `bug_report.yaml`
**Fluxo:**
- **Fast Fix**: Erros simples -> Auto-Coder corrige direto.
- **Deep Fix**: Erros lógicos/complexos -> Debugger analisa e propõe plano -> Auto-Coder executa.

---

### 🚀 Passo 7: Otimização (OPTIMIZER)
*Polimento e performance.*

**Agente:** `specialists/07-optimizer.md`
**Input:** Código estável.
**Output:** `optimization_report.yaml`, Refatorações.

**Fluxo:**
1.  Análise estática e de complexidade ciclomática.
2.  Otimização de algoritmos e queries.
3.  Melhoria de legibilidade e manutenibilidade.

---

### 🚢 Passo 8: Integração e Deploy (SYSTEM INTEGRATOR)
*Pronto para produção.*

**Agente:** `specialists/08-system-integrator.md`
**Input:** Código otimizado.
**Output:** Dockerfiles, CI/CD pipelines (GitHub Actions), Scripts de deploy.

---

### 📚 Passo 9: Documentação (DOCUMENTATION WRITER)
*Legado e transferência de conhecimento.*

**Agente:** `specialists/09-documentation-writer.md`
**Input:** Todo o projeto.
**Output:** `README.md`, Wiki, API Docs.

---

## 📂 Estrutura de Arquivos Final

```
project-root/
├── .agent/               # Configs e memórias dos agentes
├── src/                  # Código fonte (Passo 4)
├── tests/                # Testes (Passo 5)
├── docs/                 # Documentação (Passo 9)
│   ├── adr/              # Decisões Arquiteturais (Passo 3)
│   ├── strategy/         # Blueprint e Lean Canvas (Passo 0)
│   └── api/              # Specs de API
├── artifacts/            # Saídas dos Agentes (Histórico)
│   ├── strategic_blueprint.md    # Passo 0
│   ├── business_requirements.yaml # Passo 1
│   ├── user_stories.yaml         # Passo 2
│   ├── system_design.yaml        # Passo 3
│   └── ...
├── .github/workflows/    # CI/CD (Passo 8)
├── Dockerfile            # (Passo 8)
└── README.md             # (Passo 9)
```

## 🎮 Comandos do Orquestrador

- `/strategy` : Inicia o Passo 0 (Novo)
- `/start` : Inicia o Passo 1 (Assume estratégia pronta ou pula)
- `/next` : Avança o estado do projeto
- `/status` : Visualiza em qual passo o projeto está

---
*DevTeam AI - Pipeline v2.0 - Powered by Autonomous Agents*
