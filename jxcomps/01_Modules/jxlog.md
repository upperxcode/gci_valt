---
modulo: [[jxlog]]
tipo: Módulo para as mensagens e logs
status: ✅ Pronto
---

# 📝 Módulo: jxlog

## 🎯 Objetivo
Provedor de uma interface unificada de log para todo o ecossistema [[JxComps|JxComps]], substituindo o uso do `print()` padrão do Dart.

## 🚀 Como Usar
Conforme as regras rígidas do projeto, utilize os métodos estáticos para diferentes níveis de severidade:

- `JxLog.debug("Mensagem")`: Para informações de desenvolvimento.
- `JxLog.info("Mensagem")`: Fluxos normais do sistema.
- `JxLog.warn("Mensagem")`: Alertas que não interrompem o fluxo.
- `JxLog.error("Mensagem")`: Erros críticos (frequentemente usado com [[JxResultModel]]).

## 🛠️ Configuração
O sistema é configurável através de `LogSink`s para direcionar a saída (ex: console colorizado via `log_colors.dart`).

## ⚠️ Regra de Ouro
> **Nunca** utilize `print()` ou `debugPrint()` diretamente. Toda saída de terminal deve passar pelo `JxLog` para garantir padronização e rastreabilidade.
