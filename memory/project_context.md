# 🏗️ Project Context (V3.0)

Este arquivo é a **Fonte da Verdade Dinâmica** do projeto. Ele deve ser atualizado pelo Scrum Master, Architect e Tech Lead conforme o projeto evolui.

---

## 🆔 Identidade do Projeto
- **Nome**: [Nome do Projeto]
- **Versão Atual**: 0.0.1 (Alpha)
- **Descrição**: [Uma frase descrevendo o produto]

## 📍 Status Atual
- **Fase**: `Planning` / `Development` / `Release`
- **Sprint Atual**: 0
- **Meta da Sprint**: [Objetivo principal da iteração atual]

---

## 🛠️ Stack Tecnológica (Draft)
> *Preenchido pelo Software Architect (05)*
- **Frontend**: [ex: React, Vite, Tailwind]
- **Backend**: [ex: Node.js, Fastify]
- **Database**: [ex: PostgreSQL, Prisma]
- **Testing**: [ex: Vitest, Playwright]

---

## ⚖️ Invariantes do Projeto (Hard Constraints)
Estas regras não podem ser violadas por nenhum agente.

### 🔐 Segurança
1. **Zero Secrets**: NUNCA commitar chaves de API ou segredos. Use `.env`.
2. **Validation**: Todos os inputs externos devem ser validados (Zod/Joi).

### ⚡ Performance
1. **SLA**: Respostas de API < 200ms (P95).
2. **Assets**: Imagens devem ser otimizadas (WebP/AVIF).

### 💻 Código
1. **Language**: [ex: TypeScript Strict Mode]
2. **Style**: [ex: ESLint Standard, Prettier]
3. **Tests**: Cobertura mínima de 80% em lógica de negócio.

---

## 🏢 Glossário & Domínio
> *Definições compartilhadas para evitar ambiguidade.*

- **Usuário**: [Definição]
- **Cliente**: [Definição]
