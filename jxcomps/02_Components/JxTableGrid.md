---
modulo: jxwidgets
tipo: Componente Visual (jxwidgets)
status: ✅ Pronto
criado: 2026-04-24
---
# 🌐 Módulo: [[jxwidgets]]

# 🧩 Componente: JxTableGrid

## 📝 Descrição
O `JxTableGrid` é um grid de dados avançado e altamente customizável. Oferece suporte nativo a ordenação, paginação, seleção múltipla/simples, ajuste automático de largura de colunas (autoFit) e renderização customizada de células.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Configuração de Colunas:** Deve-se utilizar o modelo `JxColumn` para definir as colunas, respeitando as propriedades `width`, `autoFit` e alinhamentos adequados para cada tipo de dado (texto à esquerda, números à direita).
- [x] **Ações e Seleção:** O comportamento de seleção e interação com os dados deve ser controlado de forma robusta, muitas vezes integrando-se com `JxGridActions` para atalhos de exclusão ou edição.
- [x] **Responsividade e Performance:** Suporta renderização de listas extensas de forma eficiente e se adapta a redimensionamentos da tela/grid.

## 💻 Exemplo de Implementação
```dart
JxTableGrid(
  columns: [
    JxColumn(name: 'id', title: 'ID', width: 60, align: TextAlign.right),
    JxColumn(name: 'descricao', title: 'Descrição', autoFit: true),
  ],
  data: minhaListaDeDados,
  onRowDoubleTap: (item) => editarItem(item),
)
```

## 🔗 Relacionados
Módulo Pai: [[jxwidgets]]
Relacionado: [[JxDbActionsbar]]

