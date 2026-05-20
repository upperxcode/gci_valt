---
modulo: jxrdata
tipo: Tipagem (jxrdata)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxrdata]]

# 🧩 Componente: FieldType

## 📝 Descrição
Hierarquia de classes seladas (Sealed Class) que dita o tipo e o formato do dado transportado (`FtString`, `FtMoney`, `FtCpf`, `FtDate`, `FtTelefone`, etc.). Carrega lógicas essenciais de UI e validação primária de formato.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Validação Localizada:** Encapsula lógica de máscaras e checagens complexas utilizando frameworks parceiros como `brasil_fields` e `phone_numbers_parser`.
- [x] **Associação Automática UI:** Todo tipo determina implicitamente o ícone correspondente (`IconData get icon`) e é responsável por validar cruamente se o valor formatado é compatível.

## 💻 Exemplo de Implementação
```dart
final tipoData = const FtDate(noFuture: true, noPast: false);
final error = tipoData.validate('30/02/2026'); // Retornará erro
```

## 🔗 Relacionados
Módulo Pai: [[jxrdata]]
Relacionado: [[JxField]]

