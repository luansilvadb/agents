# 👁️ Protocolo de Observabilidade (V3.0)

Em V3.0, observabilidade não é gerar JSONs complexos que ninguém lê. É **tornar o processo de pensamento visível e auditável**.

## 1. O Princípio da Caixa de Vidro
Todo agente deve operar como uma "Caixa de Vidro" (Glass Box). O usuário deve ser capaz de entender **Por que** uma decisão foi tomada apenas lendo o histórico do chat.

### 🚫 Anti-Patterns (V2.0 Legacy)
- Logs JSON/XML gigantes no meio da conversa.
- "Pensei em X" (sem mostrar o raciocínio).
- Executar comandos silenciosamente.

## 2. Ferramentas de Observabilidade

### 2.1 Sequential Thinking (Obrigatório)
O log de raciocínio oficial do DevTeam AI é a ferramenta `mcp_sequential-thinking_sequentialthinking`.

**Quando usar:**
1. Antes de qualquer mudança de arquitetura.
2. Antes de escrever código complexo (> 20 linhas).
3. Quando encontrar um erro e precisar depurar.

**O que registrar (`thought`):**
- Hipóteses.
- Alternativas descartadas.
- Plano de ação passo-a-passo.

### 2.2 Verbose Actions
Antes de usar ferramentas de efeito colateral (`run_command`, `write_to_file`), o agente deve narrar a intenção:

> "Vou criar o arquivo `src/server.ts` com a configuração básica do Fastify para atender ao requisito de performance."

## 3. Rastreabilidade de Artefatos

Todo artefato gerado deve conter um cabeçalho de metadados simples para rastreio:

```markdown
---
_generated_by: [Agent Name]
_step: [Pipeline Step ID]
_source: [Input Artifact Name]
---
```

Isso permite saber quem criou o quê e baseado em quê.

## 4. Debugging & Status

### `/status`
O comando `/status` não deve alucinar. Ele deve listar fatos:
1. Último arquivo modificado.
2. Último passo do workflow concluído (baseado nos arquivos em `artifacts/`).

### Post-Mortem
Se um agente falhar, ele deve gerar um **Relatório de Erro** em Markdown antes de devolver o controle:

```markdown
# 💥 Falha na Execução
**Erro**: [Descrição Técnica]
**Causa Provável**: [Análise]
**Ação Recomendada**: [Intervenção Humana ou Retry]
```

---
*DevTeam AI - "See clearly, Actdecisively"*
