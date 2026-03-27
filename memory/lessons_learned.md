# 🧠 Registro de Lições Aprendidas (V5.1)

> **Nota do Sistema**: Este é o SSoT (Fonte Única da Verdade) para melhorias evolutivas do DevTeam AI.
> **Versão do Esquema**: 2.1 (Escalável e Multilíngue)

---

## 📌 Protocolo de Uso

Para garantir a escalabilidade e a precisão na recuperação de informações:

1.  🔍 **BUSQUE ANTES**: Antes de iniciar qualquer tarefa, execute uma busca por tags relacionadas (ex: `grep "#database"` neste arquivo).
2.  ⚛️ **ENTRADAS ATÔMICAS**: Mantenha as lições distintas. Use um único ID para cada conceito ou aprendizado.
3.  🆔 **IDs IMUTÁVEIS**: Uma vez atribuído, um ID (ex: `LL-001`) nunca muda. Referencie este ID em comentários de código ou PRs.
4.  📝 **FORMATO RÍGIDO**: Siga rigorosamente o template de registro para facilitar o processamento por agentes.

---

## 🏷️ Taxonomia

- **Categorias**: `[Processo]`, `[Arquitetura]`, `[Código]`, `[Estratégia]`, `[Segurança]`, `[UX]`
- **Tags**: Letras minúsculas, kebab-case, prefixadas com `#`. Exemplo: `#migration`, `#local-env`.

---

## 📚 Repositório de Lições

### 📘 LL-001: Estratégia de Desenvolvimento Local-First
- **Data**: 2026-01-05
- **Categoria**: `[Processo]`
- **Tags**: `#migration`, `#local-env`, `#velocity`
- **Contexto**: A infraestrutura da V2.0 era excessivamente complexa, com dependências remotas e Docker obrigatório, o que tornava a iteração lenta.
- **Solução**: Prioridade total para execução em `localhost` até a maturidade do software (Fase 13+).
- **Princípio Norteador**: **Limite de Otimização**: Não escale a infraestrutura antes que a lógica core esteja estável. Iterar localmente é até 3x mais rápido.

### 📗 LL-002: Estrutura de Diretórios Flat para Contexto de IA
- **Data**: 2026-01-05
- **Categoria**: `[Código]`
- **Tags**: `#file-structure`, `#ai-context`, `#colocation`
- **Contexto**: Pastas profundamente aninhadas causavam perda de contexto e confusão para os agentes de IA navegarem no código.
- **Solução**: Adoção de uma estrutura `src/` mais plana e testes colocados junto ao código (colocation).
- **Princípio Norteador**: **Topologia IA-Friendly**: Caminhos de arquivo devem ser semânticos e rasos para maximizar a precisão de recuperação de contexto.

### 📙 LL-003: Disciplina Rígida de Migração de Banco de Dados
- **Data**: 2026-01-05
- **Categoria**: `[Arquitetura]`
- **Tags**: `#database`, `#migrations`, `#stability`
- **Contexto**: Alterações diretas no DB causavam divergência de ambientes e estados inconsistentes entre desenvolvedores.
- **Solução**: Tornar mandatório o uso de migrações para TODA e QUALQUER alteração de schema.
- **Princípio Norteador**: **Schema Imutável**: O banco de dados é código. Altere-o apenas através de migrações versionadas.

### 📕 LL-004: Autoridade Máxima do Backlog de Produto
- **Data**: 2026-01-05
- **Categoria**: `[Estratégia]`
- **Tags**: `#mvp`, `#scope`, `#product-management`
- **Contexto**: Escopos abertos levavam ao "feature creep" e a alucinações de agentes sobre o que deveria ser construído.
- **Solução**: Estabelecer o `product_backlog.md` como a restrição rígida para a validade de qualquer funcionalidade.
- **Princípio Norteador**: **Autoridade de Escopo**: Se não está bem definido no Backlog, não existe no Código.

---
*Gerado pelo Sistema de Memória DevTeam AI V5.1*
