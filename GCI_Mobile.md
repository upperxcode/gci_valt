---
tags:
  - app
  - gci
  - mobile
criado: 2026-04-24
---

# 📱 GCI Mobile App

> **Resumo:** Documentação técnica da estrutura, roteamento e módulos do aplicativo front-end Flutter principal do GCI, localizado em `sindico/gci/mobile`.

## 📂 Estrutura de Diretórios (`lib/`)

O aplicativo é focado quase exclusivamente em **Views (Telas)**, **Controllers/Blocs** e **Configurações Finais**. O Core lógico reside em `gci_common`.

- **`core/`**: Configurações de tema do app final, roteamento (`GoRouter` ou equivalente), injeção de dependências central do `GetIt`, e wrappers de layout padrão (como o `MainScaffold` ou barra inferior).
- **`modules/`**: Organização por Feature/Fluxo. Cada feature detém suas próprias páginas.

## 🧩 Módulos Implementados (`modules/`)

### 1. `auth/` (Autenticação e Seleção de Perfil)
Responsável pelas telas de entrada (Login com Google, Email/Senha) e a etapa crucial de **Seleção de Perfil** (`ProfileSelectionPage`). Aqui, o usuário seleciona em qual condomínio ele deseja operar na sessão atual, chaveando o estado central do app.

### 2. `home/` (Dashboard e Feed)
A porta de entrada pós-login. Contém:
- `HomePage`: Visão geral, atalhos rápidos e métricas para síndicos.
- `NotificationsPage`: Tela que exibe os alertas vindos do `NotificationService` (do `gci_common`).

### 3. `chamados/` (Gestão de Ocorrências e Tickets)
Módulo para criação, visualização e resposta de chamados dos moradores. Interface gráfica pesada em formulários (consumindo `jxwidgets`) e listagens com filtros de status.

## 🛠️ Padrões de Implementação (App Host)

1. **Injeção de Dependência:**
   A pasta `core` abriga a inicialização do `GetIt`. O app principal é encarregado de injetar as instâncias concretas (ex: `SupabaseAuthService` em `BaseAuthInterface`), conectando o frontend ao backend real.
   
2. **Separação de Estado:**
   Toda tela complexa em `modules/` deve possuir um *Controller* ou *Store*. A tela aciona o Controller, que por sua vez chama os serviços em `gci_common`, recebe um `JxResultModel`, atualiza o estado (loading, sucesso, erro) e reflete na View.

## 🔗 Relação com JxComps

O GCI Mobile é o "cliente final" do design system. 
- A configuração do `MaterialApp` no `main.dart` herda a paleta de cores e tipografia globais definidos pelos tokens do `jxwidgets`.
- Sempre que houver uma tela com listagem, deve-se usar os utilitários de responsividade do `jxwidgets` para garantir que o layout escale caso o app rode em tablets.

---
**Páginas Relacionadas:**
- [[GCI_Overview]] - Voltar para o Guia Geral
- [[AuthService]] - Detalhes da regra de negócio por trás do login.
