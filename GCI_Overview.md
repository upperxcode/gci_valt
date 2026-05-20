---
tags:
  - sistema
  - arquitetura
  - gci
criado: 2026-04-24
---

# 🏢 Sistema GCI (Gestão Condominial Inteligente)

> **Resumo:** O GCI é a plataforma principal de gestão condominial, projetada para atender síndicos, moradores e administradoras. Este documento serve como guia mestre (Single Source of Truth) para humanos e orquestradores de IA trabalharem na base de código.

## 🏗️ Arquitetura Geral

O GCI é construído utilizando uma arquitetura modularizada, baseada no ecossistema fundacional **JxComps**. Ele separa as responsabilidades entre regras de negócio centralizadas, componentes de UI reutilizáveis e aplicativos finais (Mobile/Web).

### 🧩 Stack Tecnológica
- **Frontend:** Flutter (Mobile, Desktop, Web).
- **Backend (BaaS):** Supabase (PostgreSQL, Autenticação, Storage, Edge Functions).
- **Design System:** `jxwidgets` (interno).
- **Core Abstractions:** `jxcore`, `jxplatform`, `jxrdata`.
- **Injeção de Dependências:** `get_it`.

## 📦 Estrutura do Monorepo e Arquitetura MVC

O sistema adota uma arquitetura modular baseada em **MVC/MVVM** estrito:
- **Models:** Apenas definem dados e campos (`JxField`), sem regras de negócio (ex: `LeituraModel`).
- **Controllers:** Herdam de `JxModelController` ou `SupabaseController`. Contêm as regras de negócio, gerenciam estado para UI e se conectam com o DB online/offline (ex: `LeituraController`).
- **Views (UI):** Camada "burra" que apenas renderiza o estado usando `jxwidgets`.

### 1. Aplicações (App Hosts)
- **`sindico/gci/mobile`**: O aplicativo final principal em Flutter. Concentra a navegação, injeção de dependências finais e telas de fluxo do usuário. Mapeado em [[GCI_Mobile]].

### 2. Módulos de Domínio Compartilhado (`commom/`)
- [[gci_common]]: O coração das regras de negócio do GCI. Contém modelos (`PessoaModel`, `CondominioModel`), lógicas de autenticação central e serviços omnicanal (Push, Email).
- [[gci_leitura]]: Módulo dedicado à coleta de dados em campo. Foco em funcionar **Offline-First**, com uso potencial de OCR/ML Kit para hidrômetros.

### 3. Ecossistema Foundation (`jxcomps/`)
- [[jxcore]]: Contratos base (`BaseInterface`), classes de modelo de resultado (`JxResultModel`) e tratamento unificado de erros.
- [[jxwidgets]]: Biblioteca gráfica de botões, forms, grids e alertas. Garante a identidade visual do app.
- [[jxplatform]]: Utilitários para acesso direto aos recursos nativos do aparelho (GPS, Câmera, Rede, Permissões).

## 🚀 Fluxos Críticos do Sistema

1. **Autenticação & Multi-Tenancy:**
   O login inicia no `AuthService` (dentro de `gci_common`). O usuário pode pertencer a múltiplos condomínios. O sistema gerencia um "Condomínio Ativo" global em memória para garantir que as requisições de API (`RLS` do Supabase) retornem apenas os dados daquele escopo (Tenant).

2. **Sincronização Offline First:**
   O GCI é projetado para atuar em garagens e subsolos (onde a rede é fraca). O serviço de rede e o banco local (`sqflite`) atuam em conjunto para persistir chamados e leituras e sincronizá-los em background.

## 🤖 Regras de Ouro para IAs e Devs

- **NÃO crie lógicas de API diretamente nas telas do `mobile`.** Toda comunicação externa deve residir em `gci_common` (ou num repositório que herde de `BaseRepository`).
- **NÃO crie botões ou textfields do zero (material native).** Sempre procure um equivalente em `jxwidgets` (ex: `JxButton`, `JxTextFormField`).
- Toda resposta de serviço ou repositório **DEVE** retornar um `JxResultModel`. Nunca jogue Exceptions soltas na camada de UI.
- Acesse sempre [[manual-ia]] para lembrar as diretrizes de código limpo e regras de nomenclatura.

---
**Páginas Relacionadas:**
- [[GCI_Mobile]] - Arquitetura do App Mobile
- [[GCI_Roadmap]] - Planejamento e Entregas Pendentes
