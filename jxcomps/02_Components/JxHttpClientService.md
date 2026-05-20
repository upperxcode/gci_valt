---
modulo: jxhttpclient
tipo: Serviço de Rede (jxhttpclient)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxhttpclient]]

# 🧩 Componente: JxHttpClientService

## 📝 Descrição
Serviço centralizado para chamadas HTTP (GET, POST, etc.) com parse automático para o ecossistema e verificação de conectividade.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Conectividade:** Exige validação prévia via [[JxConnectivityHelper]].
- [x] **Tratamento de Resultados:** Respostas obrigatoriamente encapsuladas em `[[JxResultModel]]`.
- [x] **Logging:** Toda requisição deve gerar rastro via `[[JxLog]]`.

## 💻 Exemplo de Implementação
```dart
final response = await JxHttpClientService().request(
  config: JxHttpRequestConfig(url: '/endpoint', method: JxHttpMethod.get),
  parser: (data) => MeuModelo.fromJson(data),
);
if (response.isSuccess) {
  // Processar dados
}
```

## 🔗 Relacionados
Módulo Pai: [[jxhttpclient]]
Arquitetura Base: [[jxcore]]
