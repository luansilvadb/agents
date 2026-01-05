---
description: Criar documentação completa com o Agente Documentation Writer (Redator Técnico)
---

# 📚 Workflow: Agente DOCS - Redator Técnico

Este workflow aciona o agente Documentation Writer para criar documentação completa do projeto.

## Quando Usar

- Ao finalizar desenvolvimento do projeto
- Quando precisa documentar APIs
- Para criar guias de usuário
- Para documentação técnica interna

## Pré-requisitos

- Projeto implementado e funcional
- Contratos de API
- Informações de arquitetura

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\09-documentation-writer.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Código fonte do projeto
- Contratos de API
- ADRs e decisões arquiteturais
- User stories implementadas

### Passo 3: README Principal

O agente criará:
- Quick Start
- Pré-requisitos
- Instalação
- Uso básico
- Links para docs detalhada

### Passo 4: Documentação de API

O agente documentará:
- Endpoints com exemplos
- Schemas de request/response
- Códigos de erro
- Exemplos cURL

### Passo 5: Guia do Usuário

O agente criará:
- Tutoriais passo a passo
- Screenshots/diagramas
- FAQ
- Troubleshooting

### Passo 6: Documentação Técnica

O agente criará:
- Visão de arquitetura
- Modelo de dados
- Decisões técnicas
- Runbooks

### Passo 7: Projeto Completo! 🎉

Com a documentação pronta, o projeto está finalizado.

## Output Esperado

```
README.md
CHANGELOG.md
CONTRIBUTING.md

docs/
├── api/
│   └── openapi.yaml
├── architecture/
│   └── overview.md
├── user-guide/
│   └── getting-started.md
└── technical/
    └── decisions.md
```

---

*DevTeam AI - Agente Documentation Writer v1.0.0*
