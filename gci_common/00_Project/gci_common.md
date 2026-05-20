# 🏢 GCI Common - Módulo Compartilhado de Negócio

> **Resumo:** Biblioteca contendo a lógica de negócio, modelos de domínio (entidades) e serviços críticos compartilhados entre todas as frentes do ecossistema GCI (Mobile, Web, Backoffice).

## 📑 Módulos / Diretórios Principais
- **`models/`**: Entidades estruturais do banco de dados e regras de negócio (Pessoa, Condomínio, Lote, Leitura, Profile, Lookups).
- **`services/`**: Camada de serviços essenciais e integração comum (`AuthService`, `NotificationService`, `EmailService`, `ProfileService`).
- **`components/`**: Widgets visuais customizados atrelados intrinsecamente ao negócio do GCI (ex: tabelas pre-configuradas).
- **`utils/`**: Utilitários e constantes de uso global do domínio (`AppConstants`).

---

## 🛠️ Inventário de Componentes (Automático)
```dataview
TABLE tipo AS "Tipo", status AS "Status", modulo AS "Módulo"
FROM "gci/gci_common/02_Components"
WHERE contains(modulo, "gci_common")
SORT status ASC
```

## 📖 Manuais e Diretrizes

[[manual-ia]]: Regras para desenvolvimento e IAs.

[[manual]]: Documentação técnica geral.
