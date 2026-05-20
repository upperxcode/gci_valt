---
tags:
  - projeto
  - backlog
  - gci
  - visitantes
criado: 2026-04-26
---

# 🚪 Módulo de Visitantes (GCI)

> **Status:** 🚧 Planejamento Inicial
> **Objetivo:** Permitir que moradores autorizem a entrada de visitantes via QR Code e que a portaria valide esses acessos de forma integrada.

## 📋 Requisitos de Negócio
1. **Pré-autorização:** O morador cadastra nome e documento do visitante no App.
2. **QR Code:** Geração de um token único e temporário para o visitante.
3. **Log de Acesso:** Registro automático de entrada/saída na portaria.
4. **Notificação:** O morador recebe um alerta "Seu visitante chegou" no celular.

## 🏗️ Proposta Técnica

### 1. Banco de Dados (Supabase)
Tabelas necessárias:
- `visitantes`: `id`, `nome`, `documento`, `foto_url`, `condominio_id`.
- `convites`: `id`, `token` (UUID), `unidade_id`, `pessoa_id` (visitante), `expires_at`, `status` (pendente, usado, expirado).

### 2. Módulos Dart (`gci_common`)
- **Model:** `VisitanteModel`.
- **Service:** `AcessoService` (Gerencia a criação e validação de tokens).

### 3. Interface Mobile
- **Resident App:** Botão "Novo Visitante", Lista de autorizados, Gerar QR Code.
- **Porter App (ou módulo):** Leitor de QR Code para validação de entrada.

---
## 🚀 Próximos Passos
- [ ] Criar migração SQL para as novas tabelas.
- [ ] Implementar `VisitanteModel` no `gci_common`.
- [ ] Criar tela de listagem de visitantes no App Mobile.
