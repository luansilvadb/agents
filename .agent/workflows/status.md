---
description: Exibe o status atual, estado do grafo e saúde do projeto DevTeam AI
---

# Workflow: Check Project Status

Este workflow invoca o **Agente Orquestrador** para fornecer um relatório de situação.

1. **Carregar Contexto**:
   - Ler `d:\agents\orchestrator\orchestrator.md`.

2. **Inspeção de Estado**:
   - Verificar qual foi o último Agente ativo e qual o status do último Handoff (Approved/Rejected).
   - Identificar em qual Loop o projeto se encontra (Planning, Building, Release).
   - Contar métricas de "Quality Gates" (quantas vezes o código voltou para correção).

3. **Report**:
   - Gerar uma tabela Markdown ou bloco YAML resumindo o estado, similar ao exemplo `/status` do `orchestrator.md`.
   - Listar quaisquer **Blockers** ativos.
   - Listar os últimos artefatos gerados.

4. **Health Check**:
   - Validar se o processo está "travado" (muitas tentativas sem sucesso) e sugerir intervenção se necessário.
