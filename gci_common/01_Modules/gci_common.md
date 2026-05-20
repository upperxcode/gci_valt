---
modulo: gci_common
tipo: Domínio Específico (GCI)
status: ✅ Pronto
projeto: GCI
---

# 📦 Módulo: [[gci/gci_common/01_Modules/gci_common]]

## 🎯 Objetivo
Este módulo contém a lógica de negócio e modelos de dados que são partilhados exclusivamente entre os apps do ecossistema GCI (Gestão de Condomínios e Imóveis). Ele não deve ser usado em projetos fora do domínio GCI.

## 🏗️ Integração com JxComps
* **Base:** Estende as funcionalidades do [[jxcore]].
* **Rede:** Utiliza o [[jxhttpclient]] para chamadas aos endpoints específicos do back-end GCI.
* **Logs:** Segue o padrão de rastreio definido no [[jxlog]].

## 🚀 Funcionalidades Principais
* Modelos de dados globais do GCI (Imóvel, Condomínio, Utilizador GCI).
* Helpers de formatação de máscaras específicas (ex: códigos de barras de leitura).
* Tratamento de permissões de utilizador baseadas nos níveis do sistema GCI.

## ⚠️ Regras de Dependência
* Nunca deve depender de módulos de "Feature" (ex: gci_leitura). 
* É o alicerce para todos os outros módulos `gci_*`.