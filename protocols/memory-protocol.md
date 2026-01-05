# 🧠 Protocolo de Memória & Aprendizado Contínuo (v1.0)

> "Aquele que não lembra do passado está condenado a repetir bugs."

Este protocolo define como o DevTeam AI persiste conhecimento entre sessões, permitindo que os agentes "aprendam" com erros passados e mantenham o contexto do projeto vivo.

## 1. Arquitetura de Memória

O sistema utiliza um sistema de memória baseado em arquivos Markdown estruturados, simulando tipos cognitivos humanos:

### 1.1. Memória Episódica (Lessons Learned)
*   **Local**: `.agent/memory/lessons_learned.md`
*   **Propósito**: Registrar erros cometidos, soluções encontradas e padrões de sucesso.
*   **Quando escrever**: Após cada `POST-MORTEM` ou correção de bug complexo.
*   **Quando ler**: No início de cada task (`/start`) para evitar regressões.

### 1.2. Memória Semântica (Project Context)
*   **Local**: `.agent/memory/project_context.md`
*   **Propósito**: Fatos imutáveis sobre o projeto (tech stack definitivo, decisões de arquitetura, nuanças de negócio).
*   **Diferença para Docs**: Docs são para humanos; Context é "cheat sheet" para agentes.

## 2. Estrutura dos Arquivos de Memória

### Schema: Lessons Learned
```markdown
## [DATA] - [TÓPICO/CATEGORIA]
- **Contexto**: Tentamos usar a lib `x` na versão `y`.
- **Erro**: Causou conflito de dependência com `z`.
- **Aprendizado**: Para este projeto, SEMPRE usar versão `w` ou superior.
- **Trace ID**: `uuid-da-ocorrência`
```

### Schema: Project Context
```markdown
## Tech Stack Constraints
- **Framework**: Use Next.js 14+ (App Router obrigatório).
- **Estilo**: TailwindCSS apenas (NUNCA criar arquivos .css soltos).
- **Auth**: Clerk recomendado.
```

## 3. Workflow de Integração (The Recall Loop)

### Fase 1: Recall (Início da Sessão)
O **Orquestrador** deve, ao iniciar uma tarefa:
1.  Ler `.agent/memory/project_context.md`.
2.  Ler `.agent/memory/lessons_learned.md`.
3.  Injetar tópicos relevantes no contexto do Agente Especialista.

> *Prompt Injection Exemplo*: "Lembre-se: em tasks anteriores aprendemos que a API X precisa de timeout de 30s."

### Fase 2: Consolidation (Fim da Sessão/Task)
Antes de marcar uma task como `COMPLETED`, o **Orquestrador** deve perguntar ao agente:
*   "Aprendemos algo novo e reutilizável hoje?"
*   Se SIM -> Escrever em `lessons_learned.md`.

## 4. Comandos de Memória

- `/memorize [tipo] [conteudo]` - Força a gravação de um aprendizado.
- `/recall [topico]` - Busca na memória por palavras-chave.
- `/forget [id]` - (Opcional) Remove informações obsoletas.

## 5. Regras de Ouro

1.  **Não polua a memória**: Só grave *insights* reais, não logs de execução.
2.  **Seja específico**: "O banco falhou" é ruim. "O Postgres precisa de SSL: true em produção no Heroku" é bom.
3.  **Leia antes de agir**: Agentes Experts DEVEM verificar a memória antes de propor soluções arquiteturais.
