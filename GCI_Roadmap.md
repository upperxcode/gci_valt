---
tags:
  - planejamento
  - gci
  - roadmap
criado: 2026-04-24
atualizado: 2026-05-04
---

# 🛣️ Roadmap e Entregas (GCI)

> **Resumo:** Espelho do documento técnico de roadmap, indicando as *features* prontas, o que está em progresso e as pendências arquiteturais do projeto. Essencial para IAs não sugerirem refatorações em features que estão no backlog ou que acabaram de nascer.

## ✅ Concluído (Core & Módulos Base)

- **Autenticação:** Login (Google, E-mail) completo via `AuthService` e `Supabase`.
- **Multi-Tenant (Perfis):** Seleção de perfil, injetando o condomínio ativo na sessão via `ProfileService`.
- **Offline-First:** Base sólida com `sqflite` e `AutoSyncService` implementados para garantir operações offline em subsolos e garagens.
- **Ecossistema:** Todo o design system (`jxwidgets`) e infraestrutura (`jxcore`, `jxplatform`) em operação no novo formato isolado (`commom/`).
- **Storage & Infra:** Supabase integrado para storage (arquivos) e banco de dados isolado via RLS (Row Level Security).
- **Módulos Base Implementados:** `admin`, `cadastros` (moradores, veículos, unidades), `dashboard`, `leitura` (homologado para água/gás/energia) e `compras`.

## 🚧 O Que Falta Desenvolver (Elencado por Prioridades)

Orquestradores de IA operando nesta base de código **devem consultar** esta lista antes de começar a codar funcionalidades "do zero". Se a tarefa solicitar algo listado aqui, busque o planejamento ou crie a estrutura primeiro:

1. **Financeiro e Relatórios (ALTA PRIORIDADE)**
   - **Status:** Fazendo (Branch: `feat/financeiro-relatorios`).
   - **Requisitos:** PDF/CSV, avisos automáticos de vencimento e CRUD de contas. Integração pesada com backend esperada.

2. **Manutenção e Gestão de Ativos (ALTA PRIORIDADE)**
   - **Status:** Em andamento.
   - **Requisitos:** Controle de ativos, inventário do patrimônio do condomínio e gerenciamento de ordens de manutenção (ex: `AtivoController`).

3. **Módulo de Visitantes / Portaria (MÉDIA PRIORIDADE)**
   - **Status:** Planejamento (Backlog).
   - **Requisitos:** Cadastro de convidados, geração de QR Code e logs de acesso. Documentado em [[GCI_Visitantes]].

4. **MFA (Multi-Factor Authentication) (MÉDIA PRIORIDADE)**
   - **Status:** Em andamento.
   - **Requisitos:** Envolve a integração profunda no `AuthService` para biometria e OTP.

5. **Performance e Observabilidade (BAIXA PRIORIDADE)**
   - **Status:** Planejado.
   - **Requisitos:** Inclui estruturação centralizada de logs (`jxlog` futuro) e auditoria no Supabase.

6. **Testes Unitários / Widget (ACOMPANHAMENTO CONTÍNUO)**
   - **Status:** Inicialização.
   - **Regra para IAs:** Ao codar um *Service* complexo ou um *JxWidget* novo, SEMPRE inclua a suíte de testes unitários caso instruído pelo usuário, com o objetivo de buscar cobertura > 80%.

---
**Páginas Relacionadas:**
- [[GCI_Overview]] - Voltar para o Guia Geral
