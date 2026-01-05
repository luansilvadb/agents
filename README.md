# 🏢 DevTeam AI - Software House Virtual

> Sistema multiagente modular para desenvolvimento de software, seguindo arquitetura de pipeline linear.

## 📋 Visão Geral

Este sistema simula uma empresa de desenvolvimento de software com 9 agentes especializados que trabalham em sequência, cada um com responsabilidades bem definidas.

## 🔄 Pipeline de Desenvolvimento

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              PIPELINE LINEAR DE DESENVOLVIMENTO                       │
└─────────────────────────────────────────────────────────────────────────────────────┘

  ┌─────────┐    ┌─────────────┐    ┌───────────┐    ┌───────────┐    ┌────────┐
  │   ASK   │───▶│SPECIFICATION│───▶│ ARCHITECT │───▶│ AUTO-CODER│───▶│ TESTER │
  │ (BA)    │    │   WRITER    │    │           │    │   (Dev)   │    │ (QA)   │
  └─────────┘    └─────────────┘    └───────────┘    └───────────┘    └────────┘
                                                                            │
  ┌─────────────────────────────────────────────────────────────────────────┘
  │
  ▼
  ┌──────────┐    ┌───────────┐    ┌────────────┐    ┌─────────────┐
  │ DEBUGGER │───▶│ OPTIMIZER │───▶│ INTEGRATOR │───▶│DOCUMENTATION│
  │          │    │           │    │            │    │   WRITER    │
  └──────────┘    └───────────┘    └────────────┘    └─────────────┘
```

## 👥 Agentes Especialistas

| # | Agente | Função | Arquivo |
|---|--------|--------|---------|
| 1 | **Ask** | Analista de Negócios | `specialists/01-ask.md` |
| 2 | **Specification Writer** | Analista de Requisitos | `specialists/02-specification-writer.md` |
| 3 | **Architect** | Arquiteto de Software | `specialists/03-architect.md` |
| 4 | **Auto-Coder** | Desenvolvedor de Software | `specialists/04-auto-coder.md` |
| 5 | **Tester** | Engenheiro de QA (TDD) | `specialists/05-tester.md` |
| 6 | **Debugger** | Engenheiro de Software | `specialists/06-debugger.md` |
| 7 | **Optimizer** | Engenheiro de Performance | `specialists/07-optimizer.md` |
| 8 | **System Integrator** | Integrador de Sistemas | `specialists/08-system-integrator.md` |
| 9 | **Documentation Writer** | Redator Técnico | `specialists/09-documentation-writer.md` |

## 📁 Estrutura de Diretórios

```
d:\agents\
├── README.md                    # Este arquivo
├── orchestrator/
│   └── orchestrator.md          # Agente Orquestrador (PM)
├── specialists/
│   ├── 01-ask.md
│   ├── 02-specification-writer.md
│   ├── 03-architect.md
│   ├── 04-auto-coder.md
│   ├── 05-tester.md
│   ├── 06-debugger.md
│   ├── 07-optimizer.md
│   ├── 08-system-integrator.md
│   └── 09-documentation-writer.md
├── meta/
│   └── agent-template.md        # Template base para novos agentes
├── protocols/
│   └── handoff-protocol.md      # Protocolo de comunicação entre agentes
└── .agent/
    └── workflows/
        └── development-pipeline.md
```

## 🔧 Como Usar

1. **Iniciar Projeto**: Acione o Orquestrador com a demanda do cliente
2. **Pipeline Automático**: O Orquestrador coordena a passagem entre agentes
3. **Handoff Estruturado**: Cada agente produz artefatos padronizados para o próximo

## 📝 Protocolo de Handoff

Cada agente recebe e produz artefatos no formato:

```yaml
handoff:
  from: [agente_anterior]
  to: [próximo_agente]
  artifacts:
    - type: [tipo_do_artefato]
      content: [conteúdo]
  status: [ready|blocked|needs_review]
  notes: [observações]
```

## 🏷️ Versionamento

- **Sistema**: v1.0.0
- **Data**: 2026-01-05
- **Modelo de Versionamento**: SemVer (MAJOR.MINOR.PATCH)

---

*DevTeam AI - Transformando ideias em software de qualidade.*
