---
modulo: gci_common
tipo: Modelo (gci_common)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[gci/gci_common/00_Project/gci_common]]
# 🧩 Componente: CondominioModel

## 📝 Descrição
O `CondominioModel` é o coração estrutural do contexto físico. Configura os tipos e ligações relacionais dos condomínios registrados, abrangendo CNPJ, tabelas filhas e metadados de operação para que o `jxrdata` os consuma e manipule facilmente no Supabase.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Centralização da Formatação:** Nenhuma regra de exibição visual da entidade condomínio deve ser forçada nas views. Exemplo: A máscara de CNPJ, obrigatoriedade ou tipagem do CEP devem morar nativamente no `defineFields`.
- [x] **Polimorfismo Relacional:** Configurado com compatibilidade ao ecossistema de Data Access, facilitando joins com a tabela principal através do uso direto do model sem exigir tipagens manuais.

## 💻 Exemplo de Implementação
```dart
class CondominioModel extends JxModel {
  @override
  final List<JxField> defineFields = [
    JxField.of('id', FtInteger(), visible: false),
    JxField.of('razao_social', FtString(), displayName: "Razão Social"),
    // A integração e validação nativa acontecem aqui
  ];
  
  @override
  final tableName = "condominios_view";
}
```

## 🔗 Relacionados
Módulo Pai: [[gci/gci_common/00_Project/gci_common]]
Relacionado: [[jxrdata]]
