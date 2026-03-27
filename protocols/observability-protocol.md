# 👁️ Protocolo de Observabilidade Escalável (V4.2)

> **Princípio Core**: A observabilidade em sistemas multi-agente escala através da **estruturação do contexto** e da **persistência do raciocínio**. Não basta ver *o que* foi feito, precisamos entender a **árvore de decisão** que levou à ação.

---

## 1. 🧠 Sequential Thinking Pattern (Engine de Decisão)

O uso da ferramenta `mcp_sequential-thinking_sequentialthinking` é o mecanismo padrão para lidar com complexidade e garantir escalabilidade cognitiva. Ele serve como o "Córtex Frontal" auditável do agente.

### 1.1 Condições de Disparo (Trigger Conditions)
O Sequential Thinking **DEVE** ser invocado quando:
- **Mudança Arquitetural**: Alterações que afetam mais de 3 arquivos ou a estrutura do projeto.
- **Debugging Complexo**: A causa raiz de um erro não é óbvia na primeira tentativa.
- **Refatoração**: Alterações de código que visam qualidade sem mudar comportamento.
- **Planejamento de Task**: O passo inicial de qualquer demanda vaga ou de grande escopo.

### 1.2 Estrutura do Pensamento (Pattern IDA)
Cada iteração (`thought`) deve seguir o padrão **IDA** para manter a clareza:
- **I (Information)**: Quais dados tenho agora? (Leitura de arquivos, status de comandos).
- **D (Decision)**: Qual hipótese ou estratégia escolhi seguir baseada na informação?
- **A (Action)**: Qual a próxima ferramenta ou passo concreto?

### 1.3 Gestão de Branching
- Use `branchId` para testar hipóteses paralelas.
- Se um branch falhar, marque-o explicitamente no thought final e retorne ao branch principal (`main`).
- **NUNCA** deixe branches abertos sem conclusão ou veredito.

---

## 2. 🔗 Rastreabilidade Distribuída (Trace Context)

Todo artefato persistente deve manter o contexto de origem para garantir a colaboração entre múltiplos agentes e sessões.

### 2.1 Metadata Header V2 (YAML Frontmatter)
Todo arquivo de documentação, plano ou log gerado deve iniciar com este cabeçalho:

```yaml
---
id: [UUID ou Timestamp Único]
type: [artifact|plan|log|protocol]
version: 1.0.0
schema_version: 2.0
trace_parent: [ID do artefato que originou este, se houver]
agent: [Nome do Agente]
status: [draft|stable|deprecated]
context_tags:
  - domain: [ex: auth]
  - layer: [ex: infrastructure]
---
```

---

## 3. 📡 Action Streams & Logs Estruturados

A comunicação deve evoluir para **Structured Intent**. Evite prosa longa para descrições puramente técnicas.

### ✅ Padrão Recomendado (Signal)
> **Intent**: Refatorar o middleware de autenticação.
> **Target**: `src/middleware/auth.ts`
> **Impact Analysis**: Baixo risco, afeta apenas rotas protegidas.
> **Tooling**: Usarei `multi_replace_file_content` para atomicidade.

### 🚫 Anti-Pattern (Noise)
"Então, eu estava olhando aqui e acho que vou mudar o arquivo de auth porque parece melhor, vou usar a ferramenta de replace."

---

## 4. 🚑 Protocolo de Erro e Auto-Cura (Self-Healing)

Erros são inputs valiosos para o próximo ciclo de Sequential Thinking.

### 4.1 Exception Schema
Ao encontrar um erro crítico, registre o contexto estruturado:

```markdown
## ⚠️ Exception Context
- **ErrorID**: [Hash curto]
- **Component**: [Arquivo ou Módulo afetado]
- **Severity**: [Warn|Critical|Blocker]
- **Trap**: [O que causou o erro técnico ou a falha na assunção]
- **Recovery Strategy**: 
  1. [Passo imediato de mitigação/rollback]
  2. [Ação corretiva de longo prazo]
```

---

## 5. 🔍 Auditoria via `/status`

O comando `/status` deve ser **stateless**. Ele não deve confiar na memória da conversa, mas sim re-ler os metadados dos arquivos em `artifacts/` ou na estrutura do projeto para montar o relatório atual de progresso.

---
*Protocolo desenhado para Agentes Autônomos de Alta Performance - V4.2*
