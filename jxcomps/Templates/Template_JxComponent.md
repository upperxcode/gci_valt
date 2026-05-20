<%*
// Pergunta o nome do módulo apenas uma vez ao criar a nota
let modulo = await tp.system.prompt("Qual o módulo pai? (ex: jxwidgets)");
-%>
---
modulo: <% modulo %>
tipo: Componente Widget (<% modulo %>)
status: 🏗️ Em Desenvolvimento
criado: <% tp.date.now("YYYY-MM-DD") %>
---

# 🧩 Componente: <% tp.file.title %>

## 📝 Descrição
<% tp.file.cursor(1) %>

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [ ] **Tratamento de Resultados:** Utilizar e verificar retornos via [[JxResultModel]].
- [ ] **Logging:** Usar obrigatoriamente [[JxLog]] em vez de `print()`.
- [ ] **Conectividade:** Validar status via [[JxConnectivityHelper]] antes de chamadas críticas.
- [ ] **Permissões:** Requisições via [[JxPermissionHelper]].

## 💻 Exemplo de Implementação
```dart
// Exemplo de uso para o <% tp.file.title %>
```

🔗 Relacionados

- Módulo Pai: 
- Arquitetura Base: [[jxcore]]
- Repositório: [[BaseRepository]]
