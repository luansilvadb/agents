---
description: Exibe o status atual do projeto listando os artefatos gerados
---

# 📊 Project Status

Verifica o progresso do projeto listando os artefatos gerados no diretório `artifacts/`.

## Execução

```powershell
# Listar artefatos por data de modificação para ver o último passo concluído
Get-ChildItem -Path artifacts/* -File | Sort-Object LastWriteTime | Select-Object Name, LastWriteTime
```
