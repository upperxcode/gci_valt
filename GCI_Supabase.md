---
tags:
  - backend
  - supabase
  - banco-de-dados
  - gci
criado: 2026-04-24
---

# 🗄️ GCI Supabase (Backend)

> **Resumo:** O GCI utiliza o [Supabase](https://supabase.com/) como Backend-as-a-Service (BaaS) principal. Este documento cobre a modelagem, as regras de segurança (RLS) e gatilhos (Triggers) implementados no banco PostgreSQL.

## 🏗️ Estrutura do Banco de Dados

Os artefatos SQL do projeto ficam armazenados no diretório `sindico/gci/supabase/`. O banco segue a premissa de **Multi-tenant** (Múltiplas Administradoras no mesmo banco).

### Princípios de Modelagem (Identidade vs Vínculo)
1. **Identidade (`pessoas`)**: Quem é a pessoa/empresa (dados imutáveis como CPF, Nome).
2. **Vínculo (`lotes_pessoas`)**: O que a pessoa é naquele imóvel (Proprietário, Inquilino, Morador, Responsável). Resolve a relação N:N entre `lotes` e `pessoas`.

### Tabelas Principais (Core Domain)
1. **`pessoas`**: Central de usuários. Engloba síndicos, moradores e funcionários. O acesso é unificado através da trigger de criação de profile atrelada ao `auth.users` do Supabase.
2. **`condominios`**: Entidade root para um agrupamento de lotes.
3. **`lotes`**: Unidades físicas (apartamentos, casas).
4. **`lotes_pessoas`**: Tabela de associação crítica. Define quem mora, quem é dono, e mais importante: **`eh_responsavel`** (quem vota, responde legalmente e paga boletos).
5. **`leituras`**: Registra o consumo (água, gás) por lote, atrelado ao `tipo_leitura`.

### Camada de Leitura (Views API)
**Atenção Orquestradores:** O Frontend Flutter deve priorizar o consumo de **Views** para leitura de dados complexos, evitando JOINs manuais no código cliente Dart.
- **`ocupacao_view`**: Retorna dados do lote + pessoa + papéis. Usada na portaria e lista de moradores.
- **`responsaveis_view`**: Retorna apenas os responsáveis financeiros/legais. Usada para faturamento.
- **`aniversariantes_view`**: Retorna moradores aniversariando no dia para campanhas automáticas.

## 🛡️ Regras de Segurança (Row Level Security - RLS)

Como o app se comunica diretamente com o banco de dados via Supabase SDK, o **RLS (Row Level Security)** é o principal mecanismo de segurança do GCI. 

**Regra de Ouro do RLS:**
- Um usuário logado só pode efetuar leitura/escrita (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) em registros se estiver associado ao `condominio_id` daquele registro, com o privilégio adequado.
- Essas regras residem nos arquivos `regras.sql` e garantem o isolamento entre diferentes condomínios (Multi-Tenant).

## ⚡ Triggers e Funções Ativas

O projeto automatiza fluxos através do PostgreSQL:
- **`create_profile_trigger.sql`**: Assim que um usuário se cadastra no Supabase Auth (`auth.users`), esta trigger é disparada para criar automaticamente um registro na tabela pública `pessoas`. Isso assegura consistência entre o provedor de identidade e as regras de negócio.
- **`fix_login_control.sql`**: Ajustes de sessão e log de último acesso.

## 🤖 Boas Práticas para IAs e Devs

1. **Nunca crie tabelas sem RLS.** Qualquer nova tabela atrelada a domínio deve ter o RLS habilitado e uma política vinculando a um `condominio_id`.
2. **Consultas no Flutter:** Sempre que fizer queries via Supabase SDK no módulo `gci_common`, lembre-se de que o filtro `eq('condominio_id', currentCondominio)` deve ser respeitado, embora o RLS seja o muro de contenção final.
3. Se você (IA) for instruída a criar uma nova entidade (ex: `veiculos`), você **deve** criar o SQL correspondente na pasta `supabase/migrations/` (ou em um script de atualização) habilitando o RLS.

---
**Páginas Relacionadas:**
- [[GCI_Overview]] - Guia Geral do Sistema
- [[PessoaModel]] - Como a tabela `pessoas` se mapeia no Dart.
