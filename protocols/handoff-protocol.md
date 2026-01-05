# 🔄 Protocolo de Handoff entre Agentes

> Define o padrão de comunicação e transferência de artefatos entre agentes no pipeline.

---

## 1. Estrutura do Handoff

Todo handoff entre agentes DEVE seguir este formato YAML:

```yaml
handoff:
  id: "[UUID único do handoff]"
  timestamp: "[ISO 8601 timestamp]"
  
  source:
    agent: "[nome_do_agente_origem]"
    version: "[versão do agente]"
    step: [número_do_passo_no_pipeline]
  
  target:
    agent: "[nome_do_agente_destino]"
    step: [número_do_passo_no_pipeline]
  
  project:
    id: "[ID do projeto]"
    name: "[Nome do projeto]"
    iteration: [número_da_iteração]
  
  status: "[ready|blocked|needs_review|failed]"
  
  artifacts:
    - type: "[tipo_do_artefato]"
      name: "[nome_descritivo]"
      format: "[json|yaml|markdown|code]"
      path: "[caminho_do_arquivo_se_aplicável]"
      content: |
        [conteúdo inline se pequeno]
  
  validation:
    passed: [true|false]
    checks:
      - name: "[nome_da_validação]"
        status: "[pass|fail|skip]"
        message: "[mensagem explicativa]"
  
  notes: "[observações relevantes para o próximo agente]"
  
  blockers: 
    - "[lista de impedimentos se status=blocked]"
```

---

## 2. Status de Handoff

| Status | Descrição | Ação do Próximo Agente |
|--------|-----------|------------------------|
| `ready` | Artefatos prontos e validados | Processar normalmente |
| `blocked` | Há impedimentos para continuar | Resolver blockers antes de prosseguir |
| `needs_review` | Requer revisão humana ou de outro agente | Aguardar aprovação |
| `failed` | Falha crítica no processamento | Escalar para Orquestrador |

---

## 3. Tipos de Artefatos por Agente

### 3.1 Ask (Analista de Negócios)
**Output:**
- `business_requirements` - Requisitos de negócio coletados
- `stakeholder_needs` - Necessidades dos stakeholders
- `project_scope` - Escopo do projeto

### 3.2 Specification Writer (Analista de Requisitos)
**Input:** Artefatos do Ask
**Output:**
- `functional_requirements` - Requisitos funcionais detalhados
- `non_functional_requirements` - Requisitos não-funcionais
- `user_stories` - Histórias de usuário
- `acceptance_criteria` - Critérios de aceite

### 3.3 Architect (Arquiteto de Software)
**Input:** Artefatos do Specification Writer
**Output:**
- `architecture_decision_record` - ADRs (decisões arquiteturais)
- `system_design` - Design do sistema
- `component_diagram` - Diagrama de componentes
- `tech_stack` - Stack tecnológico definido
- `api_contracts` - Contratos de API

### 3.4 Auto-Coder (Desenvolvedor)
**Input:** Artefatos do Architect
**Output:**
- `source_code` - Código fonte implementado
- `code_structure` - Estrutura de arquivos criados
- `implementation_notes` - Notas de implementação

### 3.5 Tester (Engenheiro de QA)
**Input:** Artefatos do Auto-Coder + Specification Writer
**Output:**
- `test_cases` - Casos de teste
- `test_code` - Código de testes (unitários, integração)
- `test_report` - Relatório de execução
- `coverage_report` - Relatório de cobertura

### 3.6 Debugger (Engenheiro de Software)
**Input:** Artefatos do Tester (se houver falhas)
**Output:**
- `bug_analysis` - Análise de bugs encontrados
- `fix_code` - Código corrigido
- `root_cause` - Análise de causa raiz

### 3.7 Optimizer (Engenheiro de Performance)
**Input:** Artefatos do Debugger/Auto-Coder
**Output:**
- `performance_analysis` - Análise de performance
- `optimized_code` - Código otimizado
- `optimization_report` - Relatório de otimizações

### 3.8 System Integrator (Integrador de Sistemas)
**Input:** Artefatos do Optimizer
**Output:**
- `integration_config` - Configurações de integração
- `deployment_scripts` - Scripts de deploy
- `environment_setup` - Setup de ambientes

### 3.9 Documentation Writer (Redator Técnico)
**Input:** Todos os artefatos anteriores
**Output:**
- `readme` - README do projeto
- `api_docs` - Documentação de APIs
- `user_guide` - Guia do usuário
- `technical_docs` - Documentação técnica

---

## 4. Validações Obrigatórias

Cada agente DEVE validar antes de fazer handoff:

1. **Completude**: Todos os artefatos obrigatórios estão presentes
2. **Formato**: Artefatos seguem o formato especificado
3. **Consistência**: Não há contradições com artefatos anteriores
4. **Qualidade**: Atende aos critérios mínimos de qualidade do agente
5. **Ethics Check**: Em conformidade com `protocols/ethics-protocol.md`
6. **Memory Check**: Contexto atualizado conforme `protocols/memory-protocol.md`

---

## 4.1 Checkpoints Humanos (Human-in-the-Loop)

O pipeline requer validação humana explícita nos seguintes pontos:

```yaml
human_checkpoints:
  - after_step: 1  # Ask
    type: "approval"
    required: true
    description: "Validar requisitos de negócio antes da especificação"
    
  - after_step: 3  # Architect
    type: "review"
    required: true
    description: "Validar decisões de arquitetura e stack tecnológico"
    
  - after_step: 4  # Auto-Coder
    type: "optional_review"
    required: false
    description: "Revisão de código opcional antes dos testes"
    
  - after_step: 8  # System Integrator
    type: "approval"
    required: true
    description: "Aprovar configuração de deploy final"
```

---

## 5. Exemplo de Handoff Completo

```yaml
handoff:
  id: "hf-2026-01-05-001"
  timestamp: "2026-01-05T02:00:00-03:00"
  
  source:
    agent: "architect"
    version: "1.0.0"
    step: 3
  
  target:
    agent: "auto-coder"
    step: 4
  
  project:
    id: "proj-001"
    name: "Sistema de E-commerce"
    iteration: 1
  
  status: "ready"
  
  artifacts:
    - type: "architecture_decision_record"
      name: "ADR-001-Stack-Tecnologico"
      format: "markdown"
      path: "./docs/adr/ADR-001.md"
    
    - type: "system_design"
      name: "Design do Sistema"
      format: "markdown"
      content: |
        ## Arquitetura
        - Frontend: Next.js 14
        - Backend: Node.js + Express
        - Database: PostgreSQL
        - Cache: Redis
    
    - type: "api_contracts"
      name: "Contratos de API"
      format: "yaml"
      path: "./docs/api/openapi.yaml"
  
  validation:
    passed: true
    checks:
      - name: "stack_defined"
        status: "pass"
        message: "Stack tecnológico completamente definido"
      - name: "diagrams_included"
        status: "pass"
        message: "Diagramas de componentes incluídos"
  
  notes: "Priorizar implementação do módulo de autenticação primeiro. Ver ADR-001 para justificativas das escolhas tecnológicas."
  
  blockers: []
```

---

## 6. Tratamento de Erros

### 6.1 Handoff Bloqueado
Se um agente não consegue produzir artefatos válidos:
1. Definir `status: blocked`
2. Listar blockers claramente
3. Notificar Orquestrador
4. Aguardar resolução ou rollback

### 6.2 Rollback
Se necessário retornar a um passo anterior:
```yaml
rollback:
  from_step: 5
  to_step: 3
  reason: "Arquitetura incompatível com novos requisitos"
  preserve_artifacts: ["user_stories", "acceptance_criteria"]
```

---

*Protocolo de Handoff v1.0.0 - DevTeam AI*
