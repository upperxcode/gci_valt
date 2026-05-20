---
modulo: jxplatform
tipo: Helper (jxplatform)
status: ✅ Pronto
criado: 2026-04-24
---
# 🌐 Módulo: [[jxplatform]]

# 🧩 Componente: JxConnectivityHelper

## 📝 Descrição
Classe utilitária para gerenciamento e monitoramento da conexão de rede do dispositivo. Trabalha de forma reativa e pontual, permitindo não apenas checar se há internet no momento, mas também monitorar mudanças de estado continuamente.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Prevenção de Erros de Rede:** Sempre deve ser invocado pela camada de serviços HTTP (ex: `[[jxhttpclient]]`) *antes* de executar requisições pesadas, evitando timeouts e retornos sujos de socket na UI.
- [x] **Tratamento de Estado:** Telas que exigem conexão em tempo real devem usar `watchInternetConnection` para bloquear ou desbloquear a interface automaticamente.

## 💻 Exemplo de Implementação
```dart
// Verificação pontual antes de uma ação
bool hasInternet = await JxConnectivityHelper.checkInternetConnection();
if (!hasInternet) {
  JxDialogs.showWarning('Sem conexão com a internet');
  return;
}

// Monitoramento contínuo (ex: para exibir uma barra offline)
JxConnectivityHelper.watchInternetConnection().listen((isConnected) {
  print(isConnected ? "Conectado" : "Offline");
});
```

## 🔗 Relacionados
Módulo Pai: [[jxplatform]]
Relacionado: [[jxhttpclient]]
