# 🧠 Protocolo de Memória (V3.0)

A memória do DevTeam AI não é mágica, são apenas **arquivos de texto** que precisamos ler e atualizar disciplinadamente.

## 1. Arquivos Core

| Arquivo | Função | Responsável Principal | Frequência de Leitura |
| :--- | :--- | :--- | :--- |
| `project_context.md` | **Fatos do Projeto** (Stack, Regras, Fase) | Orchestrator, Scrum Master | Todo início de ciclo |
| `lessons_learned.md` | **Erros & Padrões** (O que NÃO fazer) | Tech Lead, QA, Support | Antes de tarefas complexas |

## 2. Ciclo de Leitura/Escrita

### Leitura (Recall)
Sempre que um agente for inicializado (via slash command), o **primeiro passo** do humano ou do Orquestrador deve ser garantir que o agente leu o contexto.

> **Exemplo**:
> "Olá Tech Lead, leia `project_context.md` para saber a stack e `lessons_learned.md` para ver problemas passados com ORM."

### Escrita (Commit)
Se um agente descobrir algo novo (ex: "Next.js 14 precisa dessa config específica"), ele DEVE solicitar a atualização da memória.

**Formato de Solicitação:**
```markdown
# 📝 Memory Update Request
**Arquivo**: `lessons_learned.md`
**Seção**: Tecnologia & Código
**Conteúdo**: 
- **Contexto**: Erro de Hidratação no Next.js.
- **Regra**: Componentes que usam `window` devem ser importados dinamicamente com `ssr: false`.
```

## 3. Manutenção (Jardinagem)

Memória infinita é memória inútil. O **Technical Writer (13)** é responsável por "podar" a memória:
1. Remover regras obsoletas.
2. Consolidar aprendizados duplicados.
3. Arquivar informações de versões antigas.

---
*DevTeam AI - "Context is King"*
