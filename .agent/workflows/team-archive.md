---
description: Arquivar mudanças concluídas e atualizar documentação (Fase 12-13)
---

# 📦 /team:archive

Aciona o time de especialistas para documentar a mudança e arquivar o projeto.

## 👥 Time de Finalização
- **Technical Writer**: Documentação e Knowledge Base (12)
- **Support Engineer**: Feedback e Operação (13)

## 📋 Sequência de Execução

```bash
# 12. Technical Writer (Docs-as-Code e API)
agent run specialists/process/technical_writer.md

# 13. Support Engineer (KB e Feedback Loop)
agent run specialists/process/support_engineer.md
```

## 📂 Arquivamento Estruturado

Após a documentação, a mudança é movida para o arquivo histórico:

```powershell
# Exemplo de comando para arquivamento
$archive_date = Get-Date -Format "yyyy-MM-dd"
$archive_path = "devteam/changes/archive/$archive_date-$change_id"
mkdir -p $archive_path
mv devteam/changes/$change_id/* $archive_path/
```

**Output Esperado**:
- Documentação Técnica e de Usuário em `docs/`.
- FAQ e KB atualizados para o suporte.
- Mudança movida para o histórico em `devteam/changes/archive/`.
- Repositório limpo para a próxima feature.
