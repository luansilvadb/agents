# 🧠 Protocolo de Memória Escalável (V4.0 - "Cortex")

A escalabilidade da memória depende de **Fragmentação**, **Indexação** e **Recuperação Sob Demanda**. Não tratamos a memória como um único bloco de texto, mas como um banco de dados de arquivos markdown estruturados.

## 1. Arquitetura da Memória (The Memory Bank)

A memória é organizada em camadas de volatilidade e especificidade. Os agentes devem criar e respeitar a seguinte estrutura de diretórios em `.agent/memory/` ou local equivalente:

```text
/memory
├── global/               # Contexto Imutável e Regras de Ouro
│   ├── project_manifest.md
│   └── stack_constraints.md
├── episodic/             # "Short-term": O que aconteceu recentemente
│   ├── current_sprint_context.md
│   └── active_decisions_log.md
├── semantic/             # "Long-term": Conhecimento Cristalizado
│   ├── patterns/         # Soluções reutilizáveis (Blueprints)
│   ├── troubleshooting/  # Pós-mortems e correções de erros conhecidos
│   └── adrs/             # Architecture Decision Records (Por que escolhemos X?)
└── archive/              # Memórias obsoletas (Cold Storage)
```

## 2. Padrão de Artefato (Metadados)

Para tornar a memória buscável (Scalable Search), **TODO** arquivo de memória na camada `semantic/` deve iniciar com um cabeçalho YAML (Frontmatter):

```markdown
---
id: PATTERN-AUTH-001
type: pattern | troubleshooting | adr
tags: [nextjs, auth, jwt, security]
status: active | deprecated
complexity: high
last_updated: 2024-03-20
---

# Título do Conhecimento
...
```

Isso permite que agentes usem ferramentas de busca (`grep`, `find`) para localizar "patterns sobre auth" sem ler todos os arquivos.

## 3. Protocolo de Interação (CRUD)

### 🔍 Recuperação (Search-First)
Ao invés de "Leia tudo", os agentes devem seguir o fluxo:
1. **Identificar Tópico**: "Preciso saber sobre autenticação".
2. **Buscar Tags**: Executar busca por tags ou palavras-chave na pasta `semantic/`.
3. **Ler Específico**: Ler apenas os arquivos retornados relevantes.

> **Comando de Exemplo**:
> "Busque em `memory/semantic` por arquivos contendo 'auth' e 'middleware' antes de implementar."

### 📝 Ingestão (Commit)
Quando um agente aprende algo novo:
1. **Verificar Duplicidade**: Já existe algo similar em `semantic/`?
2. **Atomizar**: Crie um arquivo pequeno e focado (ex: `troubleshooting/nextjs-hydration-error.md`), não adicione a um arquivo gigante.
3. **Indexar**: Adicione as tags corretas no frontmatter.

### 🧹 Jardinagem (Pruning)
O **Technical Writer** ou **Tech Lead** tem autonomia para:
- Mover itens de `episodic/` para `archive/` ao fim de sprints.
- Consolidar múltiplos `troubleshooting` pequenos em um `pattern` robusto.
- Marcar itens como `status: deprecated` no frontmatter.

## 4. Matriz de Responsabilidade

| Camada | Write Access (Principal) | Read Access (Principal) | Lifecycle |
| :--- | :--- | :--- | :--- |
| **Global** | Architect, Product Owner | Todos | Projeto Inteiro |
| **Episodic** | Scrum Master, Orchestrator | DevTeam (Diário) | Sprint / Ciclo |
| **Semantic** | Tech Lead, QA, Devs | DevTeam (Sob Demanda) | Permanente (Evolutivo) |

---
*DevTeam AI - "Structured Memory is Scalable Intelligence"*
