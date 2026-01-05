---
description: Configurar CI/CD e deploy com o Agente System Integrator (Integrador de Sistemas)
---

# 🔌 Workflow: Agente DEPLOY - Integrador de Sistemas

Este workflow aciona o agente System Integrator para configurar CI/CD, containers e deploy.

## Quando Usar

- Após código estar pronto para produção
- Quando precisa configurar CI/CD
- Para criar Dockerfiles e configs
- Para preparar ambientes (dev, staging, prod)

## Pré-requisitos

- Código fonte finalizado
- Stack tecnológico definido
- Informações de infraestrutura

## Como Usar

### Passo 1: Carregar o Agente

Carregue o prompt do agente:
```
d:\agents\specialists\08-system-integrator.md
```

### Passo 2: Fornecer Input

Forneça ao agente:
- Código fonte do projeto
- Stack tecnológico utilizado
- Requisitos de infraestrutura
- Plataforma de deploy (AWS, GCP, Vercel, etc.)

### Passo 3: CI/CD Pipeline

O agente criará:
- Arquivo de workflow (GitHub Actions, GitLab CI, etc.)
- Stages: build, test, security, deploy
- Gates de qualidade

### Passo 4: Containerização

O agente criará:
- Dockerfile otimizado
- docker-compose.yml
- .dockerignore

### Passo 5: Configuração de Ambientes

O agente definirá:
- Variáveis por ambiente
- Secrets necessários
- .env.example

### Passo 6: Scripts e Monitoramento

O agente criará:
- Scripts de deploy/rollback
- Health checks
- Configuração de alertas

### Passo 7: Próximo Agente

Use `/docs` para documentar o projeto.

## Output Esperado

```
.github/
└── workflows/
    └── ci-cd.yml

Dockerfile
docker-compose.yml
.env.example

scripts/
├── deploy.sh
└── rollback.sh
```

```yaml
environment_config:
  environments:
    - name: "development"
    - name: "staging"
    - name: "production"
  
  secrets_required:
    - DATABASE_URL
    - JWT_SECRET
```

---

*DevTeam AI - Agente System Integrator v1.0.0*
