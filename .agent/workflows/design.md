---
description: Criar interfaces e design system com o Agente UI/UX Designer
---

# 🎨 Workflow: Agente DESIGN - UI/UX Designer

Este workflow aciona o agente UI/UX Designer para criar interfaces, design systems e especificações visuais.

## Quando Usar

- Após ter arquitetura e personas definidas
- Quando precisa criar design system
- Para definir wireframes e layouts
- Para especificar componentes UI
- Para garantir acessibilidade

## Posição no Pipeline

```
... → ARCHITECT → UI/UX DESIGNER → AUTO-CODER → ...
         (3)          (3b)            (4)
```

O UI/UX Designer trabalha entre o Architect e o Auto-Coder.

## Pré-requisitos

- Personas definidas (do Ask)
- User stories com critérios de aceite
- Stack frontend definida (do Architect)

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\03b-ui-ux-designer.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Personas e suas necessidades
- User stories das telas a projetar
- Stack frontend (React, Vue, etc.)
- Referências visuais (se houver)
- Requisitos de acessibilidade

### Passo 3: Design System

O agente criará:
- Paleta de cores (primary, secondary, neutral, semantic)
- Tipografia (font family, scale)
- Espaçamento (spacing scale)
- Border radius e shadows
- Breakpoints responsivos

### Passo 4: Componentes

O agente definirá:
- Biblioteca de componentes (Button, Input, Card, etc.)
- Variantes de cada componente
- Estados (hover, focus, disabled)
- Especificações de acessibilidade

### Passo 5: Wireframes

O agente criará:
- Layouts das principais telas
- Fluxos de navegação
- Adaptações responsivas

### Passo 6: Interações

O agente especificará:
- Micro-interações e animações
- Estados de loading
- Feedback ao usuário (toasts, modais)

### Passo 7: Próximo Agente

Após validar, use `/code` para implementar os designs.

## Output Esperado

```yaml
design_system:
  colors: {...}
  typography: {...}
  spacing: {...}

ui_components:
  components:
    - name: "Button"
      variants: [...]
      states: [...]

wireframes:
  pages:
    - name: "Home"
      layout: {...}

accessibility_specs:
  wcag_level: "AA"
  requirements: [...]
```

## Arquivos Gerados

```
design/
├── design-system/
│   ├── tokens.yaml
│   ├── tokens.css
│   └── components.yaml
├── wireframes/
│   ├── home.yaml
│   ├── login.yaml
│   └── dashboard.yaml
└── specs/
    ├── interactions.yaml
    └── accessibility.yaml
```

## Dicas

1. **Forneça referências** - Links de sites que você gosta ajudam
2. **Especifique o tom** - Moderno? Corporativo? Divertido?
3. **Pense em acessibilidade** - Mencione requisitos específicos
4. **Considere o público** - As personas guiam as decisões

---

*DevTeam AI - Agente UI/UX Designer v1.0.0*
