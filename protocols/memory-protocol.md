# 🧠 Protocolo de Memória Escalável (V4.1 - "Cortex")

> **Princípio Core**: A escalabilidade da inteligência depende de **Fragmentação**, **Indexação** e **Recuperação Sob Demanda**. A memória não é um bloco único de texto, mas um ecossistema de arquivos estruturados e buscáveis.

---

## 1. 🏗️ Arquitetura da Memória (The Memory Bank)

A memória é organizada em camadas de volatilidade e especificidade. Os agentes devem criar e respeitar a seguinte estrutura de diretórios em `.agent/memory/` ou local equivalente:

```text
/memory
├── global/               # Contexto Imutável e Regras de Ouro
│   ├── project_manifest.md
│   └── stack_constraints.md
├── episodic/             # "Short-term": Contexto volátil da sprint/ciclo
│   ├── current_sprint_context.md
│   └── active_decisions_log.md
├── semantic/             # "Long-term": Conhecimento Cristalizado
│   ├── patterns/         # Soluções reutilizáveis e Blueprints
│   ├── troubleshooting/  # Pós-mortems e correções de erros conhecidos
│   └── adrs/             # Architecture Decision Records (O "Porquê" técnico)
└── archive/              # Memórias obsoletas (Cold Storage)
```

---

## 2. 🏷️ Padrão de Artefato (Metadados Unificados)

Para tornar a memória buscável (Scalable Search), **TODO** arquivo de memória na camada `semantic/` deve iniciar com um cabeçalho YAML alinhado ao protocolo de observabilidade:

```yaml
---
id: [MEM-ID-XXX]
type: pattern | troubleshooting | adr
version: 1.0.0
schema_version: 2.0
trace_parent: [ID do artefato de origem, se houver]
agent: [Nome do Agente que registrou]
status: active | deprecated
context_tags:
  - domain: [ex: auth]
  - technology: [ex: nextjs]
  - risk: [ex: high]
---
```

---

## 3. 🔄 Protocolo de Interação (CRUD)

### 🔍 Recuperação (Search-First)
Priorize a busca específica sobre a leitura integral do contexto. Siga o fluxo:
1. **Identifique o Tópico**: Qual o domínio da dúvida?
2. **Busque por Tags**: Execute busca por palavras-chave na pasta `semantic/`.
3. **Leia de Forma Seletiva**: Consuma apenas os arquivos retornados como relevantes.

> ✅ **Best Practice (Busca)**:
> "Busque em `memory/semantic` por arquivos contendo 'auth' e 'middleware' antes de planejar a implementação."

### 📝 Ingestão (Commit)
Quando um agente aprende algo novo ou resolve um erro crítico:
1. **Verifique Duplicidade**: Certifique-se de que não existe um pattern similar em `semantic/`.
2. **Atomize o Conhecimento**: Crie arquivos pequenos e focados. Evite arquivos gigantes "guarda-chuva".
3. **Indexe Corretamente**: Preencha rigorosamente os metadados e tags no frontmatter.

### 🧹 Jardinagem (Pruning)
O **Technical Writer** ou **Tech Lead** deve realizar a manutenção periódica:
- **Arquive**: Mova itens de `episodic/` para `archive/` ao fim de cada ciclo.
- **Consolide**: Transforme múltiplos registros de `troubleshooting` em um único `pattern` robusto.
- **Depreque**: Marque itens obsoletos como `status: deprecated`.

---

## 4. ⚖️ Matriz de Responsabilidade

| Camada | Escrita (Escritura) | Leitura (Consulta) | Ciclo de Vida |
| :--- | :--- | :--- | :--- |
| **Global** | Architect, Product Owner | Todos os Agentes | Vitalício do Projeto |
| **Episodic** | Scrum Master, Orchestrator | Time de Dev (Diário) | Ciclo/Sprint |
| **Semantic** | Tech Lead, QA, Developers | Time de Dev (Sob Demanda) | Permanente (Evolutivo) |

---
*DevTeam AI - "Structured Memory is Scalable Intelligence"*
