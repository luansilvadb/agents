# 🏗️ Manifesto e Contexto do Projeto (V5.1)

> **Fonte da Verdade**: Registro dinâmico do estado do projeto, restrições e arquitetura.
> **Última Atualização**: 2026-03-27
> **Responsáveis**: Orquestrador, Arquiteto, Tech Lead e Scrum Master.

---

## 1. 🆔 Metadados do Sistema (Metadata)

Este bloco serve como índice primário para a orientação de novos agentes e para a orquestração do pipeline.

```yaml
project_metadata:
  name: "DevTeam AI Framework"
  id: "proj-001-core"
  version: "1.0.0-stable"
  repository: "D:/agents"
  documentation_root: "docs"
  
project_config:
  language: "pt-BR"
  timezone: "America/Sao_Paulo (UTC-3)"
  agent_framework_version: "5.1.0" # Sincronizado com Handoff V5.1 e Accountability V1.1
```

---

## 2. 💓 Pulso Dinâmico (Dynamic State)

Contexto operacional atual. Esta seção deve ser atualizada em cada transição de fase ou Sprint.

```yaml
context_status:
  phase: "Documentation & Validation" # Planning | Development | Stabilization | Release
  current_sprint: 1
  sprint_goal: "Refinar e padronizar toda a documentação de protocolos e agentes para o padrão V5.1."
  system_health: "Green"
  active_blockers: 0
```

### 🎯 Entregas Chave (Sprint Atual)
- [x] Atualização dos Protocolos de Base (V5.1).
- [x] Refatoração de todos os Agentes Especialistas.
- [x] Padronização do Meta-Template de Agentes.
- [ ] Revisão do README e Guia de Onboarding.

---

## 3. 📐 Blueprint Arquitetural

### 🛠️ Tech Stack (Core)
*Consulte `memory/semantic/adrs/` para decisões técnicas detalhadas.*

```yaml
tech_stack:
  orchestration: "DevTeam AI V5.1 (Scalable Edition)"
  documentation: "Docs-as-Code (CommonMark + Mermaid)"
  standards: "Diátaxis, INVEST, SOLID, STRIDE"
  tools: "Sequential Thinking, GitHub Search, Filesystem MCP"
```

### ⚖️ Invariantes do Sistema (Não Negociáveis)
Todos os agentes **DEVEM** validar suas ações contra estas restrições rígidas.

#### 🔐 Segurança e Ética
1.  **SEGREDOS ZERO**: NUNCA commite chaves de API, senhas ou tokens. Use variáveis de ambiente mascaradas.
2.  **VALIDAÇÃO DE INPUT**: GARANTA validação estrita (Zod/Joi) em todas as fronteiras de entrada e saída.
3.  **PRIVACIDADE**: RESPEITE LGPD/GDPR. Proibido logar ou persistir PII (Dados Pessoais).

#### ⚡ Performance e Escala
1.  **RESPOSTA RÁPIDA**: MANTENHA o tempo de feedback do pipeline otimizado.
2.  **CONEXÃO DE CONTEXTO**: USE o Sequential Thinking para evitar loops e alucinações.
3.  **COMPLEXIDADE**: LIMITE a complexidade ciclomática e mantenha funções atômicas.

#### 💻 Padrões de Qualidade
1.  **LINGUAGEM**: TypeScript (Strict Mode) para código; Português Brasil para documentação.
2.  **ESTILO**: SIGA rigorosamente o guia de estilo e o linter definido.
3.  **TESTES**: EXIJA cobertura mínima de 80% em lógica de negócio.
4.  **ACCOUNTABILITY**: EMITA uma Handoff Declaration válida para cada artefato entregue.

---

## 4. 📖 Contexto de Domínio (Glossário)

- **Agente**: Entidade autônoma especialista em uma fase do pipeline.
- **Handoff**: Transição contratual de responsabilidade e artefatos.
- **Clearance**: Autorização explícita baseada em validação técnica para prosseguir.
- **DoD (Definition of Done)**: Critérios mandatórios para considerar uma tarefa concluída.

---

## 5. 🗺️ Registro do Workspace (Navegação)

Use este mapa para localizar informações detalhadas e manter a organização:

- **`.agent/memory/global/`**: Manifestos, regras de ouro e restrições de stack.
- **`.agent/memory/episodic/`**: Contexto volátil da sprint e decisões ativas.
- **`.agent/memory/semantic/`**: Conhecimento cristalizado (Patterns, ADRs, Troubleshooting).
- **`artifacts/`**: Saídas técnicas validadas prontas para consumo.
- **`specialists/`**: Definições de persona e capacidades do time.
- **`protocols/`**: Manuais de operação do sistema.

---
*DevTeam AI - "Conscious Alignment is Scalable Performance"*
