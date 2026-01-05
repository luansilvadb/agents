---
description: Implementar código de produção com o Agente Auto-Coder (Desenvolvedor de Software)
---

# 💻 Workflow: Agente CODE - Desenvolvedor de Software

Este workflow aciona o agente Auto-Coder para implementar código de produção.

## Quando Usar

- Após ter arquitetura definida
- Quando precisa implementar funcionalidades
- Para criar código seguindo contratos de API
- Para estruturar um projeto do zero

## Pré-requisitos

- Arquitetura e stack definidos
- Contratos de API especificados
- User stories para implementar
- Ou descrição clara do que codificar

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\04-auto-coder.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Design do sistema e ADRs
- Stack tecnológico definido
- Contratos de API
- Modelo de dados
- User stories a implementar

### Passo 3: Estruturação

O agente irá criar:
- Estrutura de diretórios
- Arquivos de configuração (package.json, etc.)
- Setup inicial do projeto

### Passo 4: Implementação

Monitore a implementação de:
- Componentes/módulos
- Camada de API
- Lógica de negócio
- Tratamento de erros

### Passo 5: Revisar Código

Verifique:
- Aderência aos contratos de API
- Clean code e legibilidade
- Tratamento de edge cases
- Documentação inline

### Passo 6: Próximo Agente

Após validar, use `/test` para continuar o pipeline.

## Output Esperado

```
src/
├── components/
├── services/
├── api/
├── utils/
└── index.js

implementation_notes.md
```

---

*DevTeam AI - Agente Auto-Coder v1.0.0*
