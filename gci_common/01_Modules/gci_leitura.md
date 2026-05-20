---
modulo: gci_leitura
tipo: Feature Module (GCI)
status: 🏗️ Em Desenvolvimento
projeto: GCI
---

# 📖 Módulo: [[gci/gci_common/01_Modules/gci_leitura]]

## 🎯 Objetivo
Módulo responsável por toda a lógica de recolha de dados de leitura (água, gás, energia) dentro dos apps GCI. É uma funcionalidade específica de ponta (feature).

## Quando implementado, deverá conter:
- **Modelos de Leitura:** Estruturas de dados representando os registros de consumo (medidores, fotos de relógios, histórico).
- **Serviços Específicos:** Comunicação com as APIs de leitura e persistência offline caso a leitura seja feita em áreas sem cobertura de rede.
- **Componentes Visuais:** Interfaces para os leituristas ou síndicos inserirem os dados.


## 🔗 Dependências Internas
* **Core do Domínio:** Depende obrigatoriamente do [[gci/gci_common/01_Modules/gci_common]].
* **Componentes:** Utiliza [[jxwidgets]] para os inputs de câmara e leitura de QR Codes.

## 🔗 Dependências e Relações

Espera-se que no futuro este módulo dependa de:
- [[jxcore]]: Para os contratos básicos e tratamento de retornos (`JxResultModel`).
- [[jxwidgets]]: Para uso de formulários, botões e listas padronizadas.
- [[gci/gci_common/01_Modules/gci_common]]: Para recuperar dados do usuário logado (ex: quem está realizando a leitura) e condomínio ativo.


## 🛠️ Regras de Negócio
* **Sincronização:** As leituras devem ser validadas localmente via [[gci/gci_common/01_Modules/gci_common]] antes de serem enviadas pelo [[jxhttpclient]].
* **Offline:** Deve suportar cache de dados para locais sem conectividade (ver integração com helpers de rede).

## 📂 Estrutura de Pastas (Referência)
* `/lib/src/domain`: Lógica de validação de leitura.
* `/lib/src/presentation`: telas de captura e listagem de leituras.

## 📝 Componentes (Planejados)
*(Nenhum componente específico mapeado até o momento. O módulo contém a estrutura inicial padrão do Flutter).*
