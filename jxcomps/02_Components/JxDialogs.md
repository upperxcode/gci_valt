---
modulo: jxwidgets
tipo: Utilitário UI (jxwidgets)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxwidgets]]

# 🧩 Componente: JxDialogs & Feedbacks

## 📝 Descrição
Camada unificada de utilitários visuais que encapsulam alertas, confirmações modais (`JxDialogs`) e caixas de notificação rápida (como `SnackBarMessage` e `JxToast`). 

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Alertas Destrutivos:** Sempre exibir o `JxDialogs.confirm()` antes de ações críticas como exclusão de registros ou cancelamento de fluxos importantes.
- [x] **Feedbacks de Ação:** O uso de `SnackBarMessage.success()` ou `SnackBarMessage.error()` deve ser padrão após salvar dados ou no catch de operações de rede.
- [x] **Padrão Visual Proibitivo:** É desaconselhado chamar os popups nativos do Material (`showDialog` puro ou `AlertDialog`) sem os wrappers do JxComps para garantir aderência ao Design System.

## 💻 Exemplo de Implementação
```dart
final confirmou = await JxDialogs.confirm(
  context, 
  title: 'Apagar Registro', 
  message: 'Essa operação não poderá ser desfeita. Deseja continuar?',
);

if (confirmou) {
  // Lógica de exclusão
  SnackBarMessage.success(context, 'Apagado com sucesso!');
}
```

## 🔗 Relacionados
Módulo Pai: [[jxwidgets]]

