---
modulo: jxhttpclient
tipo: Interceptor HTTP (jxhttpclient)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxhttpclient]]

# 🧩 Componente: JxHttpInterceptor

## 📝 Descrição
Interceptor da camada HTTP (baseado em Dio) que injeta automaticamente informações sobre a plataforma e gerencia o output de logs de requisições, respostas e erros.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Rastreio Centralizado:** Centraliza os prints e logs de network (ativado via `enableLogging: true`).
- [x] **Integração Nativa:** Associa automaticamente as headers `X-Device-Platform` e `X-Device-Model` obtidas via `[[JxDeviceInfoHelper]]` (módulo `jxplatform`).

## 💻 Exemplo de Implementação
```dart
// Adicionado internamente na configuração do client base
final interceptor = JxHttpInterceptor(enableLogging: true);
dio.interceptors.add(interceptor);
```

## 🔗 Relacionados
Módulo Pai: [[jxhttpclient]]
Integração: [[JxDeviceInfoHelper]], [[jxplatform]]

