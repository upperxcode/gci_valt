---
modulo: jxrdata
tipo: Entidade de Campo (jxrdata)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxrdata]]

# 🧩 Componente: JxField

## 📝 Descrição
Classe central que representa a estrutura, metadados e comportamento de um único campo do banco/interface. Engloba o estado mutável (`value`, `modified`), propriedades de UI (`width`, `align`), regras cruzadas (`JxRule`) e formatação/parse nativo.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Criação de Campos:** Sempre utilize a factory `JxField.of()` para novos campos e `JxField.from()` ao clonar instâncias.
- [x] **Validação Automática:** Concentra o comportamento de validação através do `validator()`, validando obrigatoriedade, tipos e limites numéricos ou de caracteres.
- [x] **Acesso Reativo:** Cada `JxField` gerencia seu próprio `TextEditingController` para permitir binds bidirecionais simplificados na UI.

## 💻 Exemplo de Implementação
```dart
final campoCpf = JxField.of(
  'cpf',
  const FtCpf(),
  displayName: 'CPF do Usuário',
  readOnly: false,
  notNull: true,
  validate: true,
);
```

## 🔗 Relacionados
Módulo Pai: [[jxrdata]]
Relacionado: [[JxModel]], [[FieldType]]

