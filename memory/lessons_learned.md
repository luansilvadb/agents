# 🧠 DevTeam AI V3.0 - Lessons Learned

Este documento é a **Memória Compartilhada** da equipe. Registre aqui erros superados, padrões otimizados e descobertas importantes para evitar a reinvenção da roda.

## 📌 Guia de Contribuição
- **Adicione** sempre que resolver um problema complexo.
- **Seja Conciso**: Contexto -> Solução -> Regra.
- **Categorize**: Utilize as seções abaixo.

---

## � Processo & Workflow
### [MIGRATION-V3] Transição para Desenvolvimento Local
- **Contexto**: V2.0 era excessivamente complexa com Cloud/Docker remotos.
- **Aprendizado**: Simplificar para `localhost` primeiro aumenta a velocidade de iteração em 3x.
- **Regra**: Evite infraestrutura de nuvem até que o software esteja maduro localmente (Phase 13+).

## 🛠️ Tecnologia & Código
### [GENERIC] Estrutura de Arquivos
- **Contexto**: Agentes se perdiam em pastas profundas.
- **Aprendizado**: Manter estrutura `src/` plana e modular ajuda a IA a encontrar referências.
- **Regra**: Prefira Colocation (teste junto do arquivo) ou estrutura espelhada simples.

### [DB] Migrations
- **Contexto**: Alterações diretas no banco quebravam o ambiente de outros devs.
- **Regra**: NUNCA alterar banco sem Migration. O DBA Agent é o guardião desta regra.

## 💼 Negócio & Estratégia
### [PRODUCT] Definição de MVP
- **Contexto**: Escopo aberto gerava alucinação nos agentes.
- **Regra**: O `product_backlog.md` deve ter prioridade explícita. Se não está no topo, não existe.

---
*Atualizado automaticamente pelo Sistema de Memória V3.0*
