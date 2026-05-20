---
modulo: gci_common
tipo: Serviço (gci_common)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[gci/gci_common/00_Project/gci_common]]
# 🧩 Componente: AuthService

## 📝 Descrição
O `AuthService` é o pilar de autenticação de todo o sistema GCI. Ele encapsula o cliente Supabase Auth e a integração com o Google SignIn, tratando de forma inteligente o ciclo de vida da sessão, cache local do perfil e fallback de exceções na comunicação.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Single Source of Truth:** Nunca acesse a classe do Supabase Auth diretamente nas telas; use sempre os métodos deste serviço (`handleSignIn`, `handleSignOut`, `fetchUserProfileAndValidate`) para manter o ciclo íntegro.
- [x] **Resiliência e Cache:** A busca de perfil (`fetchUserProfileAndValidate`) implementa retentativas nativas para instabilidades (502, 500) do banco de dados e fallback seguro para leitura local via `SharedPreferences`.
- [x] **Logout Seguro:** O método `handleSignOut()` garante a limpeza rigorosa do GoogleSignIn, caches temporários, dados sensíveis do ProfileService e encerramento seguro de conexão com o Supabase.

## 💻 Exemplo de Implementação
```dart
final auth = GetIt.I<AuthService>();

final profile = await auth.fetchUserProfileAndValidate(forceRefresh: true);
if (profile != null) {
  print("Bem-vindo, ${profile['nome']}");
}
```

## 🔗 Relacionados
Módulo Pai: [[gci/gci_common/00_Project/gci_common]]
