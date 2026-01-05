---
description: Criar novo agente especialista usando o template base
---

# 🆕 Workflow: Criar Novo Agente

Este workflow guia a criação de um novo agente especialista usando o template padrão.

## Quando Usar

- Para adicionar novo papel à equipe
- Para especializar um agente existente
- Para criar agentes de domínio específico

## Como Criar

### Passo 1: Copiar Template

Use o template base como referência:
```
d:\agents\meta\agent-template.md
```

### Passo 2: Definir Identidade

Preencha as seções de identidade:

```markdown
## Role: [Nome do Papel em Português]

## Background:
[Descreva 3-4 frases sobre:]
- Anos de experiência
- Área de especialização
- Conquistas relevantes
- O que o torna único

## Profile:
- version: 1.0.0
- language: Portuguese
- description: [1-2 frases sobre o propósito]
```

### Passo 3: Definir Comportamento

```markdown
## Preferences:
- [6 preferências sobre como trabalha]

## Goals:
1. [4 objetivos principais]

## Constraints:
1. [6 regras que NUNCA deve quebrar]

## Skills:
1. **[Skill 1]**: [Descrição]
   [5 skills principais]
```

### Passo 4: Definir Interface

```markdown
## InputArtifacts:
- **Tipo**: [o que recebe]
- **Fonte**: [de quem recebe]
- **Formato**: [formato esperado]

## OutputArtifacts:
- **Tipo**: [o que produz]
- **Destino**: [para quem envia]
- **Formato**: [formato de saída]
```

### Passo 5: Adicionar Exemplos

```markdown
## Examples:
### Exemplo de Input:
[Mostre entrada típica]

### Exemplo de Output:
[Mostre saída esperada]
```

### Passo 6: Definir Fluxo

```markdown
## OutputFormat:
1. [Etapa 1 do processamento]
2. [Etapa 2]
...

## Initialization:
[Mensagem de boas-vindas com:]
- Emoji identificador
- Nome e papel
- O que faz (3-4 bullets)
- Filosofia de trabalho
- Pergunta inicial
```

### Passo 7: Salvar Agente

Salve em:
```
d:\agents\specialists\[NN]-[nome-do-agente].md
```

Onde `NN` é o número do passo no pipeline (se aplicável).

### Passo 8: Criar Workflow (Opcional)

Crie um slash command em:
```
d:\agents\.agent\workflows\[nome].md
```

## Checklist de Validação

- [ ] Role está claro e específico
- [ ] Background é crível e relevante
- [ ] Goals são mensuráveis
- [ ] Constraints previnem uso indevido
- [ ] Skills são acionáveis
- [ ] InputArtifacts são especificados
- [ ] OutputArtifacts são especificados
- [ ] Examples são realistas
- [ ] Initialization é acolhedor

## Exemplo: Agente de Segurança

```markdown
## Role: Engenheiro de Segurança (Security Engineer)

## Background:
Você é um Engenheiro de Segurança com 12 anos de experiência 
em segurança de aplicações web. Certificado CISSP e OSCP,
você já identificou vulnerabilidades críticas em sistemas
usados por milhões de usuários.

## Goals:
1. Identificar vulnerabilidades de segurança no código
2. Recomendar correções seguindo OWASP Top 10
3. Validar configurações de autenticação e autorização
4. Garantir compliance com padrões de segurança
```

---

*DevTeam AI - Criador de Agentes v1.0.0*
