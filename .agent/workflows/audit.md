---
description: Executar auditoria de qualidade e alinhamento do projeto
---

# Workflow: Auditoria de Alinhamento e Qualidade (/audit)

Este workflow aciona o Agente de Alinhamento e Qualidade para verificar a consistência do projeto.

## Passos

1. **Carregar Agente Auditor**
   - Ler o perfil do agente em: `d:\agents\specialists\99-alignment-auditor.md`

2. **Coletar Contexto do Projeto**
   - Listar arquivos na raiz e pastas de documentação principais.
   - Ler `README.md` e arquivos de especificação recentes para estabelecer a "verdade base".

3. **Executar Auditoria**
   - Enviar prompt para o agente iniciar a varredura.
   - Solicitar verificação de:
     - Consistência entre documentos.
     - Links quebrados.
     - Desvios entre spec e código (se houver código).

4. **Gerar Relatório**
   - O agente deve produzir o relatório de alinhamento.
   - Salvar relatório (opcional) ou apresentar no chat.

## Exemplo de Uso

> "Execute o /audit para verificar se todos os documentos de requisitos estão refletidos na arquitetura atual."
