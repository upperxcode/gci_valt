---
modulo: jxwidgets
tipo: Layout Component (jxwidgets)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxwidgets]]

# 🧩 Componente: JxDbActionsbar

## 📝 Descrição
Barra de botões de ações padronizada focada em contextos de banco de dados (Salvar, Novo, Editar, Excluir, Voltar). Ela condensa atalhos essenciais na mesma linguagem visual.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Responsabilidade de Layout:** Injetada costumeiramente em telas de listagem base (`GridPageBase`) ou formulários (`CadPageBase`).
- [x] **Gerenciamento de Estados:** Seus botões desabilitam automaticamente de acordo com o contexto injetado; o botão "Excluir", por exemplo, pode não ser exibido ou ficar desabilitado caso o registro atual seja uma nova inserção (`isNew`).
- [x] **Design Adaptativo:** A barra comprime os rótulos de texto, tornando-se icon-only em resoluções mais estreitas (ex: mobile).

## 💻 Exemplo de Implementação
```dart
JxDbActionsbar(
  onSave: () async {
    if (form.validate()) {
      await salvar();
    }
  },
  onDelete: permitirDelete ? () => apagar() : null,
  onCancel: () => Navigator.of(context).pop(),
  isNewRecord: isNew, // Controla se botões como excluir estão visíveis
)
```

## 🔗 Relacionados
Módulo Pai: [[jxwidgets]]
Relacionado: [[JxForm]], [[JxTableGrid]]

