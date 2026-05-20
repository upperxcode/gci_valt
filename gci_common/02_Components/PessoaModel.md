---

modulo: gci_common

tipo: Modelo (gci_common)

status: ✅ Pronto

criado: 2026-04-24

---
# 🌐 Módulo: [[gci/gci_common/00_Project/gci_common]]

# 🧩 Componente: PessoaModel
  

## 📝 Descrição

O `PessoaModel` estende o contrato base `JxModel` (do `jxrdata`) e atua como espelho da view `pessoas_view` do banco de dados, estabelecendo as tipagens rígidas e validações exigidas para perfis físicos e jurídicos.

  
## 🛠️ Diretrizes Obrigatórias (Manual JxComps)

- [x] **Automação de Formatadores:** A injeção nativa de tipos como `FtCpfCnpj()` e `FtTelefone()` dentro da lista `defineFields` acopla as máscaras diretamente à entidade, isentando a UI (Formulários) de precisar mapeá-las na renderização visual.

- [x] **Acesso Restrito:** Utiliza os parâmetros de metadados como `sensitive: true` e `visible: false` para restringir instantaneamente campos da visualização em `[[JxTableGrid]]` no sistema de Backoffice.

  

## 💻 Exemplo de Implementação

```dart

class PessoaModel extends JxModel {

@override

final List<JxField> defineFields = [

JxField.of('id', FtInteger(), visible: false),

JxField.of('nome', FtString(), displayName: "Nome"),

JxField.of('cpf_cnpj', FtCpfCnpj(), sensitive: true),

JxField.of('telefone', FtTelefone(), sensitive: true),

];

@override

final tableName = "pessoas_view";

}

```

  

## 🔗 Relacionados

Módulo Pai: [[gci/gci_common/00_Project/gci_common]]

Relacionado: [[jxrdata]]
