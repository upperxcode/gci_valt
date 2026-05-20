---
modulo: jxplatform
tipo: Helper (jxplatform)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxplatform]]

# 🧩 Componente: JxDeviceInfoHelper

## 📝 Descrição

Módulo responsável por extrair metadados detalhados de hardware e sistema operacional da plataforma em que o aplicativo está rodando. Centraliza a lógica de mapeamento dos dados extraídos pelo plugin `device_info_plus`.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)

- [x] **Mapeamento de Erros e Telemetria:** Extremamente útil na geração de payloads para serviços de log (`[[jxlog]]`) e Sentry, onde se anexa o modelo do aparelho e a versão do OS à causa raiz de um bug reportado.
- [x] **Abstração Multiplataforma:** A função `getDeviceDetails()` já trata internamente todas as bifurcações de plataforma (web, android, ios, windows, etc). O desenvolvedor só precisa pedir os dados e tratar o mapa resultante.

## 💻 Exemplo de Implementação

```dart
final details = await JxDeviceInfoHelper.getDeviceDetails();

print(details['platform']); // ex: "android"

if (details['platform'] == 'android') {
  print("Modelo: ${details['model']}");
  print("Marca: ${details['brand']}");
}
```

## 🔗 Relacionados

Módulo Pai: [[jxplatform]]
Relacionado: [[JxPlatformType]], [[jxlog]]
