---
modulo: jxcore
tipo: Modelo Abstrato (jxcore)
status: ✅ Pronto
criado: 2026-04-24
---
# 🌐 Módulo: [[jxcore]]
# 🧩 Componente: JxResultModel

## 📝 Descrição
O `JxResultModel` é o padrão absoluto de resposta para todas as operações assíncronas ou críticas do ecossistema JxComps. Ele encapsula o sucesso, falha e dados retornados de uma função em um envelope seguro, inibindo crashes por exceções não tratadas na UI.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Substituição do Throw:** Serviços e repositórios não devem quebrar o fluxo com `throw` para a tela. Devem sempre encapsular o erro retornando `JxResultModel.error(message: '...')`.
- [x] **Uniformidade:** Toda requisição da camada de rede (`[[jxhttpclient]]`) ou operação de banco já retorna esse modelo nativamente.
- [x] **Boas Práticas de Leitura:** A verificação de sucesso deve ser sempre feita através da propriedade `.isSuccess`, ao invés de comparações manuais do status enum.

## 💻 Exemplo de Implementação
```dart
Future<JxResultModel<String>> processarPagamento() async {
  try {
    // Processo longo
    return JxResultModel.success("Sucesso!");
  } catch (e) {
    return JxResultModel.error(message: 'Falha no processamento: $e');
  }
}

// Na chamada:
final result = await processarPagamento();
if (result.isSuccess) {
  // sucesso
} else {
  JxDialogs.showError(result.message);
}
```

## 🔗 Relacionados
Módulo Pai: [[jxcore]]
Relacionado: [[jxhttpclient]], [[BaseRepository]]

