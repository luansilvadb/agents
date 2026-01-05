---
description: Iniciar novo projeto via Agente Orquestrador (Project Manager)
---

# 🎯 Workflow: Iniciar Novo Projeto

Este workflow aciona o Agente Orquestrador para gerenciar um projeto completo através do pipeline.

## Quando Usar

- Para iniciar um projeto do zero
- Quando quer gestão automática do pipeline
- Para acompanhar progresso entre agentes
- Para ter visibilidade do status do projeto

## Como Usar

### Passo 1: Carregar o Orquestrador

Carregue o prompt do orquestrador:
```
d:\agents\orchestrator\orchestrator.md
```

### Passo 2: Iniciar Projeto

Use o comando:
```
/start [descrição da demanda do cliente]
```

Exemplo:
```
/start Preciso de um sistema de e-commerce para vender artesanato online
```

### Passo 3: Acompanhar Pipeline

O Orquestrador irá:
1. Inicializar tracking do projeto
2. Acionar o Agente Ask (Passo 1)
3. Validar handoffs entre agentes
4. Avançar automaticamente no pipeline
5. Reportar status

### Comandos Disponíveis

| Comando | Descrição |
|---------|-----------|
| `/start [demanda]` | Inicia novo projeto |
| `/status` | Mostra status atual |
| `/next` | Avança para próximo agente |
| `/rollback [step]` | Retorna a passo anterior |
| `/block [motivo]` | Registra blocker |
| `/resolve [id]` | Resolve blocker |
| `/agents` | Lista status dos agentes |
| `/artifacts` | Lista artefatos produzidos |

### Passo 4: Interagir com Agentes

Quando o Orquestrador acionar um agente, você irá:
1. Responder perguntas do agente
2. Validar artefatos produzidos
3. Aprovar para prosseguir

### Passo 5: Monitorar Progresso

Use `/status` para ver:
```
📊 Status do Projeto: [Nome]

Passo Atual: 4/9 - AUTO-CODER
Status: ✅ In Progress

| Passo | Agente | Status |
|-------|--------|--------|
| 1 | Ask | ✅ Completed |
| 2 | Specification Writer | ✅ Completed |
| 3 | Architect | ✅ Completed |
| 4 | Auto-Coder | 🔄 In Progress |
| 5-9 | ... | ⏳ Pending |
```

### Passo 6: Projeto Completo

Quando todos os 9 passos forem concluídos:
- Documentação estará pronta
- CI/CD configurado
- Código testado e otimizado

## Estrutura Final do Projeto

```
projeto/
├── src/                    # Código fonte
├── tests/                  # Testes
├── docs/                   # Documentação
├── .github/workflows/      # CI/CD
├── artifacts/              # Artefatos do pipeline
├── Dockerfile
├── docker-compose.yml
├── README.md
└── CHANGELOG.md
```

## Dicas

1. **Seja detalhado** na demanda inicial
2. **Valide cada handoff** antes de prosseguir
3. **Use /status** frequentemente
4. **Documente desvios** se precisar ajustar algo

---

*DevTeam AI - Orquestrador v1.0.0*
