---

modulo: gci_common

tipo: Serviço (gci_common)

status: ✅ Pronto

criado: 2026-04-24

---

  

# 🌐 Módulo: [[gci/gci_common/00_Project/gci_common]]

# 🧩 Componente: NotificationService

  

## 📝 Descrição

Serviço orquestrador do sistema de notificações (Mensageria e Avisos) do condomínio. Gerencia desde disparos unitários em push, leitura constante de notificações não lidas (polling), até broadcast em massa de Campanhas.

  

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)

- [x] **Polling Automático:** Componentes visuais como os "sininhos" de alerta do app não precisam buscar os dados manualmente; basta utilizar o *ChangeNotifier* alimentado pela leitura em background no `startPolling()`.

- [x] **Integração Omnichannel:** Os disparos (`createNotification` ou `broadcastCampaign`) abstraem e lidam intrinsecamente com as vias disponíveis no ambiente (Push nativo, E-mail, ou Webhook do WhatsApp).

  

## 💻 Exemplo de Implementação

```dart

final notifService = GetIt.I<NotificationService>();

  

// Disparar uma notificação push unitária

await notifService.createNotification(

userId: '123',

title: 'Nova Encomenda',

body: 'Você recebeu um pacote na portaria.',

channel: 'push'

);

  

// Ler o contador de forma reativa no widget

print("Total Não lidas: ${notifService.unreadCount}");

```

  

## 🔗 Relacionados

Módulo Pai: [[gci/gci_common/00_Project/gci_common]]