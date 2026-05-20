---
modulo: jxcore
tipo: Abstração de Erro (jxcore)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxcore]]

# 🧩 Componente: JxExceptions & Error Bases

## 📝 Descrição
Arquivos com classes e abstracts voltados para a estruturação de exceções conhecidas. Atua como utilitário para quando a camada mais profunda necessita estourar um erro que será interceptado (catch) e transformado em um `[[JxResultModel]]` mais acima.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Tipificação Forte:** Proíbe o disparo solto de erros não tipados (`throw Exception()`). Obriga o uso de classes derivadas que portem descrições semânticas.
- [x] **Integração de Logs:** Toda classe de exceção do sistema foi concebida para conversar diretamente com o [[jxlog]], fornecendo stack traces organizados em níveis de criticidade e rastreabilidade para o Sentry/Crashlytics.

## 💻 Exemplo de Implementação
```dart
class JxDataValidationException implements Exception {
  final String fieldName;
  final String errorMessage;

  JxDataValidationException(this.fieldName, this.errorMessage);

  @override
  String toString() => "Validação Falhou [$fieldName]: $errorMessage";
}
```

## 🔗 Relacionados
Módulo Pai: [[jxcore]]
Relacionado: [[jxlog]]

