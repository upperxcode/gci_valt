---
tags:
  - documentacao
  - jxwidgets
  - gci
criado: 2026-04-26
---

# 🛠️ Relatório de Gestão de Componentes

Este documento atua como o inventário e guia de manutenção dos componentes da biblioteca `jxcomps` e sua implementação no GCI.

## 📦 Inventário de Componentes (jxwidgets)

| Categoria | Componente | Status | Responsabilidade |
|-----------|------------|--------|-------------------|
| **Formulários** | `JxTextField`, `JxForms`, `JxValidators` | ✅ Estável | Inputs padronizados com validação JxCore |
| **Botões** | `JxButtons`, `JxElevatedButton`, `JxOutlineButton` | ✅ Estável | Tipografia e cores do Design System GCI |
| **Listas/Grids** | `JxTableGrid`, `JxTableGridPage`, `JxDbActionsbar` | 🚧 Em Refatoração | Tabelas dinâmicas com injeção de ações de DB |
| **Navegação** | `JxNavigatorBar`, `JxAppBar` | ✅ Estável | Gestão de rotas e AppBar customizada |
| **Diálogos** | `JxDialogs`, `JxNotifications` | ✅ Estável | Snackbars e Popups com JxResultModel |
| **Seleção** | `JxComboBox`, `JxFormComboBox` | ✅ Estável | Dropdowns integrados ao JxrData |

## 📐 Padrões de Manutenção
1. **Isolamento**: Nenhuma regra de negócio deve estar no widget. Use Controllers.
2. **Resultados**: Widgets de ação devem disparar eventos que retornem `JxResultModel`.
3. **Estilo**: Proibido uso de `Colors.*` ou `TextStyle` nativo. Use `JxAppStyle`.

---

# 🤖 Guia para Agentes
Ao modificar qualquer componente acima, certifique-se de que a alteração seja retrocompatível com os módulos `gci_common` e `gci_leitura`.
