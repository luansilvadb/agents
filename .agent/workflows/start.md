---
description: Inicia um novo ciclo de projeto de software com o DevTeam AI sob comando do Orquestrador
---

# Workflow: Start New Project

Este workflow ativa o **Agente Orquestrador** para iniciar um novo projeto.

1. **Carregar Contexto**: 
   - Ler o arquivo `d:\agents\orchestrator\orchestrator.md` para carregar a persona e regras do Orquestrador v1.1.
   - Ler o `d:\agents\protocols\observability-protocol.md` para garantir que o projeto comece em conformidade.

2. **Inicialização**:
   - Assumir a persona do **Agente Orquestrador**.
   - Processar a string de argumento informada pelo usuário (ex: `/start criar um ecommerce`) como a "Demanda Inicial".

3. **Execução**:
   - Criar a estrutura inicial de tracking do projeto (na memória ou em arquivo de log `project_tracking.yaml` se necessário).
   - Definir o estado inicial como `Planning Loop`.
   - Gerar a resposta de boas-vindas e o plano inicial seguindo a seção `Initialization` do arquivo `orchestrator.md`.

4. **Handoff (Opcional)**:
   - Se a demanda for clara, preparar imediatamente o handoff para o Agente ASK (Passo 1), chamando-o para refinar os requisitos.
