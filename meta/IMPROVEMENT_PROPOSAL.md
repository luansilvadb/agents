# 🚀 Proposta de Evolução: DevTeam AI v2.0

Baseado em uma pesquisa profunda sobre **Arquiteturas de Agentes Autônomos (2024-2025)** e melhores práticas de Engenharia de Software Multi-Agente, apresento esta proposta de atualização para o ecossistema DevTeam AI.

## 📊 Diagnóstico do Sistema Atual (v1.x)

### ✅ Pontos Fortes
- **Arquitetura Híbrida**: O Orquestrador já implementa corretamente um Grafo de Estados (não puramente linear), o que é estado da arte.
- **Protocolos de Qualidade**: O uso de *Chain of Thought* (Raciocínio) e *Observabilidade* no Auto-Coder e Tester está muito à frente de implementações básicas.
- **Handoff Estruturado**: O protocolo YAML garante integridade na passagem de bastão.

### ⚠️ Oportunidades de Melhoria (Gaps)
1.  **Fadiga de Contexto no Chat**: O protocolo de handoff atual exige colar YAMLs extensos na conversa. Isso consome tokens e "polui" a memória de curto prazo do modelo.
2.  **Abstração de Ferramentas**: Os agentes sabem "o que" fazer (Skills), mas não têm instruções explícitas de "como" usar as ferramentas do ambiente (Tools MCP como `run_command`, `write_to_file`) de forma otimizada.
3.  **Loop Tester-Coder Manual**: O ciclo de correção de bugs (Tester -> Debugger -> Coder) parece burocrático. A tendência atual é "Self-Correction" rápida.
4.  **Falta de "Grounding"**: Não há um passo explícito de verificação do ambiente (checar versões de Node, Python, Docker) antes de iniciar, o que gera erros de execução comuns.

---

## 💡 Plano de Ação: DevTeam AI v2.0

### 1. Gestão de Estado Centralizada (Single Source of Truth)
Substituir (ou complementar) os handoffs via chat por um arquivo de estado vivo.

*   **Novo Artefato**: `.agent/project_state.json`
*   **Funcionamento**: Os agentes leem e escrevem o status neste arquivo. No chat, comunicam apenas: *"Atualizei o estado para `TESTING_FAILED`. Veja detalhes em `project_state.json`."*
*   **Benefício**: Redução drástica de uso de tokens e persistência real do progresso.

### 2. Protocolo "Fast-Fix" (Loop Cíclico Autônomo)
Autorizar o **Tester** a rejeitar diretamente para o **Auto-Coder** (sem passar pelo Debugger para erros triviais) ou permitir que o **Auto-Coder** execute seus próprios testes preliminares.

*   **Mudança**: Adicionar etapa `Pre-Commit Check` no Auto-Coder.
*   **Fluxo**: `Auto-Coder` -> `Escreve Código` -> `Roda Teste Rápido` -> `Passou?` -> `Handoff`.

### 3. Definição Explícita de Toolbelt
Adicionar uma seção `## Toolbelt` em cada prompt de agente, mapeando skills para ferramentas reais do sistema.

*   **Exemplo (Auto-Coder)**:
    ```markdown
    ## Toolbelt:
    - **Criar Arquivos**: Use `write_to_file` (preferencialmente blocos completos).
    - **Listar Arquivos**: Use `list_dir` para entender a estrutura antes de criar.
    - **Validar Sintaxe**: Use `run_command` com linters (ex: `eslint`).
    ```

### 4. Novo Agente: "Environment Specialist" (Opcional ou Skill do Integrador)
Um especialista (ou fase inicial) que garante que o ambiente de execução local está apto a receber o código.

*   **Responsabilidade**: Rodar `npm install`, verificar `node -v`, garantir que o banco de dados está de pé.

---

## 📅 Roadmap Sugerido

1.  **Fase 1 (Core)**: Criar o arquivo `project_state.json` e atualizar o prompt do **Orchestrator** para gerenciá-lo.
2.  **Fase 2 (Tools)**: Atualizar prompts do **Architect** e **Auto-Coder** com a seção `Toolbelt`.
3.  **Fase 3 (Autonomy)**: Implementar o script de `Fast-Fix` nos workflows.

Deseja que eu inicie a implementação da **Fase 1** agora?
