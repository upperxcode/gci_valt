---
modulo: jxhttpclient
tipo: Tratamento de Erros (jxhttpclient)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxhttpclient]]
# 🧩 Componente: Exceções HTTP (JxBaseException)

## 📝 Descrição
Hierarquia de exceções personalizadas focadas no ecossistema de rede, cobrindo de problemas de infraestrutura a retornos inválidos da API.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Tipagem:** Todas as exceções do módulo (`JxHttpNetworkException`, `JxHttpClientException`, `JxHttpTimeoutException`) estendem `JxBaseException`.
- [x] **Encapsulamento:** Utilizadas internamente pelo cliente para devolver falhas formatadas corretamente no padrão `[[JxResultModel]]`.

## 💻 Exemplo de Implementação
```dart
try {
  // execução de chamadas manuais
} on JxHttpNetworkException catch (e) {
  print('Falha na rede: ${e.message} (Status: ${e.statusCode})');
}
```

## 🔗 Relacionados
Módulo Pai: [[jxhttpclient]]
Resultados: [[JxResultModel]]
