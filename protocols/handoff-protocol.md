# Protocolo de Handoff (V3.0)

Este protocolo define a cadeia de custódia dos artefatos. Para que o pipeline funcione, cada etapa deve entregar **exatamente** o que a próxima etapa espera.

> **Regra de Ouro**: "Garbage In, Garbage Out". Se o artefato de entrada for ruim, REJEITE-O imediatamente para o agente anterior.

## 1. Matriz de Handoff

| Passo Atual | Agente (Origem) | Artefato Gerado (Output) | Próximo Passo | Agente (Destino) | Validação Esperada |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **01** | Product Manager | `product_backlog.md` | **02** | Scrum Master | Lista priorizada existe? |
| **02** | Scrum Master | `sprint_plan.md` | **03** | Business Analyst | Meta da sprint clara? |
| **03** | Business Analyst | `detailed_specifications.md` | **04** | System Analyst | Critérios de aceite Gherkin? |
| **04** | System Analyst | `technical_specifications.md` | **05** | Architect | Contratos de API/Dados? |
| **05** | Architect | `architecture_design.md` | **06** / **07** | UI/UX & Security | Stack definida? |
| **06** | UI/UX Designer | `ui_design_system.md` | **07** | Security Design | Mockups/Tokens existem? |
| **07** | Security Design | `security_policies.md` | **08** | Tech Lead | Threat Model definido? |
| **08** | Tech Lead | `implementation_plan.md` | **09** | Senior Developer | Tarefas < 1 dia? |
| **09** | Senior Developer | `src/*` (Código) | **10** / **11** | DBA & QA | Compila/Roda? |
| **10** | DBA | `database/*` (Schema) | **11** | QA Engineer | Migrations rodam? |
| **11** | QA Engineer | `test_report.md` | **12** | Security Validation | Passou nos testes? |
| **12** | Security Val | `security_validation_report.md` | **13** | Tech Writer | Sem vulns críticas? |
| **13** | Tech Writer | `docs/*` | **14** | Support Engineer | Docs legíveis? |
| **14** | Support Engineer | `user_feedback_report.md` | **01** | Product Manager | Insights para V2? |

## 2. Mecânica de Rejeição

Se um agente receber um artefato inválido (ex: `specs` sem critérios de aceite), ele deve:

1. **NÃO processar** a tarefa.
2. Escrever um relatório de rejeição no formato:
   ```markdown
   # REJECTED: [Nome do Artefato]
   **Motivo**: O artefato está incompleto.
   **Faltando**: Critérios de aceite na história #12.
   **Ação**: Devolvendo para [Agente Anterior].
   ```
3. O Orquestrador reiniciará o passo anterior.

## 3. Definição de "Pronto" (DoD)

Um handoff só é válido se:
1. O arquivo existe no caminho correto (`artifacts/` ou `docs/` ou `src/`).
2. O conteúdo não é um placeholder ("Lorem Ipsum").
3. O formato (Markdown/Code) está sintaticamente correto.

---
*DevTeam AI - Pipeline Integrity Protocol*
