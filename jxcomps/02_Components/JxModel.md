---
modulo: jxrdata
tipo: Modelo de Dados (jxrdata)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxrdata]]

# 🧩 Componente: JxModel

## 📝 Descrição
Classe base abstrata para criação de modelos de dados reativos. Faz o mapeamento entre campos estruturados (`[[JxField]]`) e as propriedades do banco de dados/JSON, além de suportar reatividade nativa via `ListenableBuilder`.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Definição de Campos:** Toda classe filha deve implementar o getter `defineFields` retornando uma lista de `[[JxField]]`.
- [x] **Nome da Tabela:** A propriedade `tableName` deve ser sobrescrita obrigatoriamente para mapeamento.
- [x] **Serialização:** O modelo deve suportar as factory functions `fromJson` e `fromFields` para integrar adequadamente com a infraestrutura de dados.

## 💻 Exemplo de Implementação
```dart
class UsuarioModel extends JxModel {
  UsuarioModel([super.incomingFields]);

  @override
  String get tableName => 'usuarios';

  @override
  List<JxField> get defineFields => [
        JxField.of('id', const FtInteger(), readOnly: true),
        JxField.of('nome', const FtString(), validate: true),
      ];
}
```

## 🔗 Relacionados
Módulo Pai: [[jxrdata]]
Relacionado: [[JxField]], [[JxModelController]]

