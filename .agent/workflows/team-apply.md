---
description: Implementar mudanças aprovadas com o time de Execução (Fase 8-11)
---

# 🛠️ /team:apply

Aciona o time de especialistas para implementar e validar o código de uma proposta aprovada em `devteam/changes/[id]`.

## 👥 Time de Execução
- **Senior Developer**: Implementação do Código (09)
- **QA Engineer**: Testes Unitários e E2E (10)
- **Security Validation Engineer**: Validação Final de Segurança (11)

## 📋 Sequência de Execução

```bash
# 9. Senior Developer (Codificação e Unit Tests)
agent run specialists/engineering/senior_developer.md

# 10. QA Engineer (Validação Funcional e QA)
agent run specialists/quality/qa_engineer.md

# 11. Security Validation (Gatekeeper de Segurança)
agent run specialists/quality/security_validation_engineer.md
```

## ✅ Validação de Entrega

Após a execução, os artefatos são atualizados:

```powershell
# Exemplo de comando para validação final
mv artifacts/08_tech_plan.md $path/implementation_plan.md
mv artifacts/10_test_report.md $path/validation/qa_report.md
mv artifacts/11_security_validation.md $path/validation/security_report.md
```

**Output Esperado**:
- Código Fonte atualizado em `src/`.
- Testes Unitários e Integração em `tests/`.
- Relatórios de Validação em `validation/`.
- Plano de Implementação concluído.
