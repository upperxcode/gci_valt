---
tags:
  - modulo
  - gci_leitura
criado: 2026-04-24
---

# 📖 Módulo gci_leitura

> **Resumo:** Este módulo destina-se a encapsular as funcionalidades e fluxos relacionados à leitura de consumos (água, gás, etc.) ou outras formas de leituras contínuas do sistema GCI.

## 🧭 Propósito Atual

Atualmente, o módulo encontra-se em estágio inicial de scaffolding (estruturação básica). O objetivo arquitetural para este módulo é isolar o domínio de "Leitura", mantendo-o desacoplado do aplicativo principal e do núcleo comum (`gci_common`).

Quando implementado, deverá conter:
- **Modelos de Leitura:** Estruturas de dados representando os registros de consumo (medidores, fotos de relógios, histórico).
- **Serviços Específicos:** Comunicação com as APIs de leitura e persistência offline caso a leitura seja feita em áreas sem cobertura de rede.
- **Componentes Visuais:** Interfaces para os leituristas ou síndicos inserirem os dados.

## 🔗 Dependências e Relações

Espera-se que no futuro este módulo dependa de:
- [[jxcore]]: Para os contratos básicos e tratamento de retornos (`JxResultModel`).
- [[jxwidgets]]: Para uso de formulários, botões e listas padronizadas.
- [[gci_common]]: Para recuperar dados do usuário logado (ex: quem está realizando a leitura) e condomínio ativo.

## 📝 Componentes (Planejados)
*(Nenhum componente específico mapeado até o momento. O módulo contém a estrutura inicial padrão do Flutter).*
