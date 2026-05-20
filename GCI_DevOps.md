---
tags:
  - scripts
  - devops
  - gci
criado: 2026-04-24
---

# ⚙️ GCI Scripts e DevOps

> **Resumo:** Guia de utilização dos scripts utilitários e infraestrutura de desenvolvimento contidos no diretório `sindico/gci/scripts`.

## 🛠️ Scripts Disponíveis

Os scripts automatizam as tarefas repetitivas do dia a dia. Todos devem ser executados a partir da raiz do projeto (`sindico/gci/`).

### 1. `./scripts/run`
**Propósito:** Inicia o ambiente de desenvolvimento.
O servidor de desenvolvimento do Flutter (e integrações periféricas) geralmente é lançado através deste orquestrador. Ele cuida de rodar o app principal (`mobile`) enquanto escuta mudanças.
- *Uso pela IA:* Se for necessário reiniciar a aplicação após mudanças massivas de dependências, este é o script ativo que precisa ser monitorado.

### 2. `./scripts/clean`
**Propósito:** Limpa os builds, caches e executa `flutter pub get` nos pacotes do ecossistema.
Altamente útil quando se tem o erro clássico de "Target of URI doesn't exist" decorrente da refatoração de módulos como o `jxcomps` ou `gci_common`.
- *Uso:* Rode `./scripts/clean` sempre que mudar a estrutura do monorepo.

### 3. `./scripts/setup-linux-deep-link`
**Propósito:** Configura o ambiente Linux local para aceitar Deep Links do Supabase Auth (ex: link mágico por email).
Essencial para testes locais de login/recuperação de senha quando o desenvolvedor está operando em uma máquina Linux.

## 🚢 CI/CD e Build (Futuro)

Conforme descrito no [[GCI_Roadmap]], o pipeline de automação de testes, CI/CD (GitHub Actions) e publicação nas lojas (App Store / Play Store) encontram-se em estágio de **planejamento**.

Quando estas ferramentas forem introduzidas, este documento será o responsável por ditar:
1. Como assinar os APKs/AABs e IPAs.
2. Como lidar com as variáveis de ambiente (DotEnv) de Prod vs Staging.
3. Estruturas de *Fastlane*, caso venham a ser utilizadas.

---
**Páginas Relacionadas:**
- [[GCI_Overview]] - Guia Geral
- [[GCI_Roadmap]] - Acompanhamento das Entregas
