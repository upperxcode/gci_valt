---
modulo: jxrdata
tipo: Controlador Reativo (jxrdata)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxrdata]]

# 🧩 Componente: JxModelController

## 📝 Descrição
Controlador de estado (estende `ChangeNotifier`) que funciona como orquestrador entre a tela, o modelo `[[JxModel]]` e a fonte de dados (`JxDataSource`). Fornece métodos padronizados de CRUD reativo (`load`, `save`, `refresh`, `reset`).

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Gerenciamento de Estado:** Notifica a árvore de widgets via `notifyListeners()` a cada alteração, cuidando isoladamente do estado global de progresso (`isLoading`).
- [x] **Desacoplamento de Dados:** Depende da interface `JxDataSource`, mantendo o controlador ignorante em relação a se a fonte é um BD local, Supabase ou API Rest.
- [x] **Auto-Refresh:** Dispõe de rotinas embutidas para varreduras silenciosas da fonte (`silentRefresh`) para checar se houve mudança no backend.

## 💻 Exemplo de Implementação
```dart
final controller = JxModelController<UsuarioModel>(
  model: UsuarioModel(),
  dataSource: MeuDataSourceRemote(),
  modelFactory: (fields) => UsuarioModel(fields),
);

// Na UI:
await controller.load('123-uuid');
```

## 🔗 Relacionados
Módulo Pai: [[jxrdata]]
Relacionado: [[JxModel]], [[JxTextField]]

