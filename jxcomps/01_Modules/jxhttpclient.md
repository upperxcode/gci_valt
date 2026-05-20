---
modulo: jxhttpclient
tipo: Camada de Rede
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: jxhttpclient

## 🎯 Objetivo
Abstração de alto nível para chamadas HTTP, baseada no `JxHttpClientService` e configurada via `JxHttpRequestConfig`. Garante um tratamento padronizado para conectividade, logs e parse automático de dados para o ecossistema.

## ⚙️ Configurações de Rede
* **BaseURL:** Configuração centralizada do endpoint da API.
* **Headers:** Gerenciamento de tokens de autenticação e Content-Type.
* **Timeout:** Definição de tempos de espera para requisições.

## 🚀 Funcionalidades e Regras
* **Tratamento de Resultados:** Toda resposta é convertida automaticamente para o padrão [[JxResultModel]].
* **Logging:** Integração nativa com o [[jxlog]] para rastreamento de requests e responses.
* **Resiliência:** Tratamento embutido para exceções como `NoInternetException`.

## 🛠️ Diretrizes Obrigatórias
* Antes de qualquer chamada, deve-se validar o status da conexão usando o [[JxConnectivityHelper|helper de conectividade]].
* Utilizar obrigatoriamente as chamadas padronizadas (GET, POST, etc.) do serviço para garantir a consistência dos logs.

## 🔗 Relacionados
* **Arquitetura Base:** [[jxcore]]
* **Sistema de Log:** [[jxlog]]
* **Conectividade:** [[JxConnectivityHelper]]
