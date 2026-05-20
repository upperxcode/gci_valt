---
modulo: [[jx_core]]
tipo: Módulo principal
status: ✅ Pronto
---

# 📦 modulo: jxcore

## 🎯 Objetivo
Núcleo do ecossistema JxComps. Fornece utilitários essenciais, modelos de resposta padrão e os contratos de arquitetura que todos os outros módulos devem seguir.

## 🏛️ Contratos e Classes Base
- [[BaseInterface]]: Contrato genérico para serviços.
- [[BaseRepository]]: Contrato base para repositórios de dados (Local/Remoto).
- [[JxResultModel]]: Padrão obrigatório de retorno para operações (`isSuccess`, `data`, `message`).

## 🛠️ Utilitários do Core
- **Validadores:** Enums globais como `PlatformType`.
- **Exceções:** Classes base para tratamento resiliente de erros.

## 📋 Regras de Ouro
1. Toda operação de repositório deve implementar [[BaseRepository]].
2. Todo retorno de função assíncrona deve ser encapsulado em um [[JxResultModel]].
