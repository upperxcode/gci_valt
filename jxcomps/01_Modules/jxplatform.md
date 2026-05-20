---
modulo: [[jxplatform]]
tipo: Módulo para controle da plataforma de execução
status: ✅ Pronto
---

# 📱 Módulo: jxplatform

## 🎯 Objetivo
Facilita o acesso a recursos nativos e informações específicas do hardware/dispositivo.

## 🛠️ Helpers Disponíveis
- **[[JxPlatformHelper]]**: Detecta a plataforma (Android, iOS, Web).
- **[[JxDeviceInfoHelper]]**: Obtém especificações do hardware.
- **[[JxConnectivityHelper]]**: Verifica status da internet (Obrigatório em chamadas de rede).
- **[[JxPermissionHelper]]**: Gerenciamento simplificado de permissões (Câmera, GPS, etc).

## 📋 Diretriz
Antes de qualquer operação que dependa de rede, valide usando `JxConnectivityHelper.checkInternetConnection()`.
