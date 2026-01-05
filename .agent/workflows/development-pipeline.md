---
description: Pipeline completo de desenvolvimento com agentes especializados
---

# 🔄 Workflow: Pipeline de Desenvolvimento

Este workflow descreve como usar a equipe de agentes DevTeam AI para desenvolver um projeto do zero.

## Pré-requisitos

- Demanda/ideia do cliente claramente definida
- Acesso aos arquivos de prompt dos agentes em `d:\agents\specialists\`

## Pipeline de Execução

### Passo 1: Análise de Negócios (ASK)

**Agente:** `specialists/01-ask.md`

**Input:** Descrição inicial do cliente
**Output:** `business_requirements.yaml`

**Ações:**
1. Carregue o prompt do agente Ask
2. Forneça a demanda inicial do cliente
3. Responda às perguntas do agente (mínimo 5 trocas)
4. Valide o resumo de requisitos de negócio
5. Salve o artefato `business_requirements.yaml`

---

### Passo 2: Especificação de Requisitos (SPECIFICATION WRITER)

**Agente:** `specialists/02-specification-writer.md`

**Input:** `business_requirements.yaml`
**Output:** `user_stories.yaml`, `non_functional_requirements.yaml`

**Ações:**
1. Carregue o prompt do agente Specification Writer
2. Forneça os requisitos de negócio do passo anterior
3. Revise as user stories geradas
4. Valide os critérios de aceite
5. Salve os artefatos de especificação

---

### Passo 3: Arquitetura (ARCHITECT)

**Agente:** `specialists/03-architect.md`

**Input:** `user_stories.yaml`, `non_functional_requirements.yaml`
**Output:** `adrs/`, `system_design.yaml`, `api_contracts.yaml`, `data_model.yaml`

**Ações:**
1. Carregue o prompt do agente Architect
2. Forneça as especificações do passo anterior
3. Revise as decisões arquiteturais (ADRs)
4. Valide o stack tecnológico escolhido
5. Confirme contratos de API e modelo de dados
6. Salve os artefatos de arquitetura

---

### Passo 4: Implementação (AUTO-CODER)

**Agente:** `specialists/04-auto-coder.md`

**Input:** Todos artefatos do Architect + User Stories
**Output:** Código fonte (`src/`), `implementation_notes.md`

**Ações:**
1. Carregue o prompt do agente Auto-Coder
2. Forneça arquitetura e especificações
3. Monitore a implementação por módulos
4. Revise código gerado para cada componente
5. Valide aderência aos contratos de API
6. Salve código fonte e notas de implementação

---

### Passo 5: Testes (TESTER)

**Agente:** `specialists/05-tester.md`

**Input:** Código fonte + User Stories + Acceptance Criteria
**Output:** `tests/`, `test_report.yaml`, `bug_report.yaml`

**Ações:**
1. Carregue o prompt do agente Tester
2. Forneça código e critérios de aceite
3. Aguarde criação da suíte de testes
4. Revise relatório de execução
5. Identifique bugs encontrados
6. Se houver bugs, prossiga para Passo 6
7. Se não houver bugs, pule para Passo 7

---

### Passo 6: Correção de Bugs (FAST-FIX CYCLE)

**Agentes:** `specialists/04-auto-coder.md` (Fast Fix) OU `specialists/06-debugger.md` (Complex Fix)

**Input:** `bug_report.yaml` e falhas de teste.

**Lógica de Decisão:**
1. **Erro Simples** (Sintaxe, Typos, Regras triviais):
    - O **Tester** rejeita diretamente para o **Auto-Coder** (`status: REJECTED_FAST`).
    - O **Auto-Coder** corrige e re-submete sem passar pelo Debugger.
    - *Economia de tempo e tokens.*

2. **Erro Complexo** (Lógica de Negócio, Concorrência, Vazamento de Memória):
    - O **Tester** rejeita com `status: REJECTED_COMPLEX`.
    - Ativa o **Debugger** para análise de causa raiz profunda.
    - **Debugger** gera `fix_plan.yaml` para o Auto-Coder.

**Ações (Fast-Fix):**
1. Auto-Coder recebe relatório de falha.
2. Aplica correção imediata (`replace_file_content`).
3. Roda teste local (`npm test`).
4. Passou? Submete novamente ao Tester.

**Ações (Complex-Fix):**
1. Debugger analisa logs e stack trace.
2. Isola o problema e propõe solução arquitetural.
3. Auto-Coder implementa a solução robusta.
4. Retorna ao Tester.

---

### Passo 7: Otimização (OPTIMIZER)

**Agente:** `specialists/07-optimizer.md`

**Input:** Código fonte + NFRs de performance
**Output:** Código otimizado, `optimization_report.yaml`

**Ações:**
1. Carregue o prompt do agente Optimizer
2. Forneça código e requisitos de performance
3. Aguarde análise de baseline
4. Revise otimizações propostas
5. Valide benchmarks antes/depois
6. Confirme compliance com NFRs
7. Salve código otimizado

---

### Passo 8: Integração (SYSTEM INTEGRATOR)

**Agente:** `specialists/08-system-integrator.md`

**Input:** Código final + Stack tecnológico
**Output:** CI/CD config, Dockerfile, docker-compose, scripts

**Ações:**
1. Carregue o prompt do agente System Integrator
2. Forneça código e configurações de stack
3. Revise pipeline CI/CD gerado
4. Valide Dockerfiles e configs de ambiente
5. Teste scripts de deploy localmente
6. Salve configurações de integração

---

### Passo 9: Documentação (DOCUMENTATION WRITER)

**Agente:** `specialists/09-documentation-writer.md`

**Input:** Todos os artefatos anteriores
**Output:** `README.md`, `docs/`, API docs, User Guide

**Ações:**
1. Carregue o prompt do agente Documentation Writer
2. Forneça todos os artefatos do projeto
3. Revise README principal
4. Valide documentação de API
5. Confirme guia do usuário
6. Salve toda documentação
7. **Projeto completo! 🎉**

---

## Estrutura de Artefatos Esperada

Ao final do pipeline, você deve ter:

```
projeto/
├── src/                      # Código fonte (Passo 4)
├── tests/                    # Testes (Passo 5)
├── docs/
│   ├── adr/                  # Decisões arquiteturais (Passo 3)
│   ├── api/                  # Documentação de API (Passo 9)
│   └── user-guide.md         # Guia do usuário (Passo 9)
├── artifacts/
│   ├── business_requirements.yaml    # Passo 1
│   ├── user_stories.yaml            # Passo 2
│   ├── non_functional_requirements.yaml  # Passo 2
│   ├── system_design.yaml           # Passo 3
│   ├── api_contracts.yaml           # Passo 3
│   ├── data_model.yaml              # Passo 3
│   ├── test_report.yaml             # Passo 5
│   ├── bug_report.yaml              # Passo 5
│   ├── fix_report.yaml              # Passo 6
│   └── optimization_report.yaml     # Passo 7
├── .github/
│   └── workflows/            # CI/CD (Passo 8)
├── Dockerfile                # (Passo 8)
├── docker-compose.yml        # (Passo 8)
├── README.md                 # (Passo 9)
└── CHANGELOG.md              # (Passo 9)
```

## Comandos do Orquestrador

Para usar o Orquestrador (`orchestrator/orchestrator.md`):

- `/start [demanda]` - Inicia novo projeto
- `/status` - Mostra status do pipeline
- `/next` - Avança para próximo agente
- `/rollback [step]` - Retorna a passo anterior
- `/agents` - Lista status dos agentes

## Dicas

1. **Não pule passos** - Cada agente depende dos artefatos do anterior
2. **Valide antes de prosseguir** - Erros propagam pelo pipeline
3. **Documente desvios** - Se precisar ajustar algo, documente
4. **Itere se necessário** - Pode voltar a passos anteriores
5. **Use o Orquestrador** - Ele ajuda a manter o controle

---

*DevTeam AI - Pipeline de Desenvolvimento v1.0.0*
