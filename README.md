# 🏢 DevTeam AI v2.0 - Software House Autônoma

> Sistema multiagente híbrido para desenvolvimento de software, com gestão de estado centralizada e correção cíclica.

## 📋 Visão Geral

Este sistema simula uma empresa de desenvolvimento de software de alta performance. Diferente de pipelines lineares simples, o **DevTeam AI v2.0** opera com **Single Source of Truth** (Project State) e possui loops de "Fast-Fix" para correção rápida de erros.

## 🔄 Arquitetura Híbrida (V2.0)

O pipeline combina fluxo linear para definição com ciclos de feedback rápidos para construção.

```
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│                           PIPELINE HÍBRIDO DE DESENVOLVIMENTO                           │
└─────────────────────────────────────────────────────────────────────────────────────────┘

  PLANNIG PHASE:
  ┌───────┐    ┌─────────────┐    ┌───────────┐
  │  ASK  │───▶│SPECIFICATION│───▶│ ARCHITECT │
  └───────┘    └─────────────┘    └───────────┘
                                        │
                                        ▼
  BUILD PHASE (Cyclic):           ┌───────────┐    ⚡ Fast-Fix Loop
  ┌──────────────────────────────▶│ AUTO-CODER│◀──────────────┐
  │                               └───────────┘               │
  │                                     │                     │
  │                                     ▼                     │
  │                               ┌───────────┐        ┌─────────────┐
  │           Complex Fix Loop    │  TESTER   │───────▶│ FAILED_FAST │
  └───────────────────────────────│ (Quality) │        └─────────────┘
                                  └───────────┘
                                        │
                                        ▼
  RELEASE PHASE:                  ┌────────────┐    ┌─────────────┐
                                  │ INTEGRATOR │───▶│DOCUMENTATION│
                                  └────────────┘    └─────────────┘
```

## ✨ Novidades da Versão 2.0

1.  **Gestão de Estado Centralizada**: O arquivo `.agent/project_state.json` mantém o status real do projeto, evitando perda de contexto no chat.
2.  **Toolbelts Explícitos**: Agentes agora possuem instruções concretas de sistema (ex: `write_to_file`, `run_command`, `npm test`) em vez de apenas skills abstratas.
3.  **Fast-Fix Cycle**: O Tester pode rejeitar bugs triviais diretamente para o Auto-Coder, economizando tempo e tokens.
4.  **Shift-Left Testing**: O Auto-Coder valida seu próprio código antes de submeter.

## 👥 Agentes e Responsabilidades

| ID | Agente | Função | Foco Principal |
|----|--------|--------|----------------|
| -- | **Orchestrator** | Gerente de Projeto | Gestão de Estado e Coordenação |
| 00 | **Product Strategist** | Estrategista de Produto | Visão, Roadmap e Alinhamento de Negócio |
| 01 | **Ask** | Analista de Negócios | Levantamento e Refinamento de Requisitos |
| 02 | **Specification Writer** | Especificador Técnico | Transformação de Requisitos em Specs Técnicas |
| 03 | **Architect** | Arquiteto de Software | Decisões de Design (ADRs) e Estrutura |
| 03b| **UI/UX Designer** | Designer | Design System, Interfaces e Usabilidade |
| 03c| **Security Engineer** | Eng. de Segurança | Análise de Vulnerabilidades e Proteção |
| 04 | **Auto-Coder** | Desenvolvedor | Implementação (Shift-Left) e Refatoração |
| 05 | **Tester** | QA Engineer | Testes Unitários, Integração e E2E |
| 06 | **Debugger** | Eng. de Software | Análise de Logs e Correção de Bucks Complexos |
| 07 | **Optimizer** | Eng. de Performance | Otimização de Código e Recursos |
| 08 | **System Integrator** | DevOps/SRE | Pipelines CI/CD e Deploy |
| 09 | **Documentation Writer** | Tech Writer | Documentação Viva e Manuais |
| 99 | **Alignment Auditor** | Auditor | Garantia de Consistência e Verdade Única |

## 🔧 Como Usar

O sistema é controlado pelo **Orquestrador**. Não é necessário configurar o editor manualmente.

1.  **Carregue o Orquestrador**: Abra `orchestrator/orchestrator.md` como System Instruction.
2.  **Inicie**: Digite `/start "Descrição do seu projeto de software"`.
3.  **Siga o Fluxo**: O Orquestrador instruirá quando trocar de agente (ex: "Carregue `01-ask.md` agora").
4.  **Monitore**: Veja o progresso em `.agent/project_state.json`.

## 📁 Estrutura Atualizada

```
d:\agents\
├── .agent/
│   ├── project_state.json       # 🧠 Single Source of Truth
│   └── workflows/               # Workflows definidos
├── orchestrator/                # Gerente do Projeto
├── specialists/                 # Agentes com Toolbelts atualizados
└── artifacts/                   # Saída gerada (Código, Docs, Testes)
```

## 🏷️ Versionamento

- **Sistema**: v2.0.0
- **Release**: Hybrid Architecture & State Management
- **Data**: 2026-01-05

---

*DevTeam AI - Transformando ideias em software com inteligência autônoma.*
