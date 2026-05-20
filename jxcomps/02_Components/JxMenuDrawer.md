---
modulo: jxwidgets
tipo: Componente Visual (jxwidgets)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxwidgets]]

# 🧩 Componente: JxMenuDrawer

## 📝 Descrição
O `JxMenuDrawer` é o componente central para layout de navegação lateral (drawer) para as aplicações do ecossistema. Suporta aninhamento em múltiplos níveis (submenus recolhíveis) e mantém estados de rota ativa.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Acessibilidade e Layout:** O menu normalmente é amarrado à propriedade `drawer` do `Scaffold` no mobile, ou utilizado como painel flexível em interfaces Desktop.
- [x] **Estrutura Mapeada:** Os itens da lista devem ser obrigatoriamente passados através das entidades fornecidas pelo framework (como `JxMenuItem`), garantindo que ícones, labels e rotas tenham visuais unificados.

## 💻 Exemplo de Implementação
```dart
Scaffold(
  drawer: JxMenuDrawer(
    items: [
      JxMenuItem(icon: Icons.dashboard, title: 'Painel', route: '/home'),
      JxMenuItem(
        icon: Icons.people,
        title: 'Cadastros',
        children: [
          JxMenuItem(title: 'Clientes', route: '/clientes'),
          JxMenuItem(title: 'Fornecedores', route: '/fornecedores'),
        ],
      ),
    ],
  ),
  body: MainContent(),
)
```

## 🔗 Relacionados
Módulo Pai: [[jxwidgets]]

