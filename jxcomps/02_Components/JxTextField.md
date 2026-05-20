---
modulo: jxrdata
tipo: Widget Reativo (jxrdata)
status: ✅ Pronto
criado: 2026-04-24
---
# 🌐 Módulo: [[jxrdata]]

# 🧩 Componente: JxTextField

## 📝 Descrição
Componente visual de formulário (StatefulWidget) projetado para consumir diretamente propriedades de um `[[JxModelController]]` e o seu respectivo `[[JxField]]`. Lida automaticamente com as máscaras, ícones e teclado adequados.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Bind Bi-Direcional:** A propriedade `fieldName` e o `modelController` se mantém sincronizados; alterações na UI sobem para o Field, alterações no Field refletem na tela.
- [x] **Privacidade Inteligente:** Adota regras automáticas de alternância de visibilidade de campo (olho) baseados em propriedades de segurança (`FtPassword` ou marcadores de proteção LGPD).
- [x] **Formatação Independente:** Resolve magicamente o `TextInputFormatter` ideal e o `TextInputType` lendo apenas o `[[FieldType]]` associado no modelo.

## 💻 Exemplo de Implementação
```dart
JxTextField(
  modelController: meuController,
  fieldName: 'cpf',
  label: 'Digite o CPF',
  validationMode: AutovalidateMode.onUserInteraction,
)
```

## 🔗 Relacionados
Módulo Pai: [[jxrdata]]
Relacionado: [[JxModelController]], [[JxField]]

