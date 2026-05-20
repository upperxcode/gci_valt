---
modulo: jxwidgets
tipo: Componente Visual (jxwidgets)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxwidgets]]

# 🧩 Componente: JxForm

## 📝 Descrição
O `JxForm` e o utilitário `JxFormController` abstraem o gerenciamento padrão de formulários do Flutter (`GlobalKey<FormState>`). Eles cuidam de estados internos de validação e submissão em telas de cadastro complexas.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Controlador Dedicado:** O `JxFormController` deve ser instanciado e repassado ao `JxForm`, garantindo acesso programático seguro aos métodos `validate()` sem a necessidade de acessar os builders ou chaves da árvore manualmente.
- [x] **Integração de Entradas:** Os inputs customizados (`JxTextField`, `JxComboBox`, etc.) já reportam seus erros de validação nativamente para a engine do `JxForm`.

## 💻 Exemplo de Implementação
```dart
final formController = JxFormController();

JxForm(
  controller: formController,
  child: Column(
    children: [
      JxTextField(label: 'Nome Completo', notNull: true),
      JxButton(
        text: 'Gravar',
        onPressed: () {
          if (formController.validate()) {
            // Executa requisição
          }
        },
      )
    ],
  ),
)
```

## 🔗 Relacionados
Módulo Pai: [[jxwidgets]]
Relacionado: [[JxDbActionsbar]]

