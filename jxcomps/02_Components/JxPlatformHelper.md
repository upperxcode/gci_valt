---
modulo: jxplatform
tipo: Helper (jxplatform)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxplatform]]
# 🧩 Componente: JxPlatformHelper

## 📝 Descrição
Fornece métodos síncronos e rápidos para identificação do ambiente e natureza da plataforma em execução (Mobile, Web, Desktop). Muito útil na orquestração de rotas, adaptação de layouts ou habilitação condicional de botões nativos.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Velocidade e Sincronismo:** Atua em tempo de execução quase instantâneo lendo macros (`kIsWeb`, `Platform`), ou seja, diferentemente de ler as informações do *device*, aqui não há `await`. Perfeito para ser usado diretamente dentro da árvore de widgets (`build`).
- [x] **Camadas Visuais:** Preferido para o uso na camada de exibição (ex: mudar o fluxo de navegação se `isMobile` para não renderizar grids super densas que pertenceriam ao formato `isDesktop`).

## 💻 Exemplo de Implementação
```dart
@override
Widget build(BuildContext context) {
  if (JxPlatformHelper.isMobile) {
    return MobileDashboardLayout();
  } else if (JxPlatformHelper.isWeb) {
    return WebDashboardLayout();
  }
  
  // Imprime a plataforma textual ("android", "ios", "windows"...)
  print(JxPlatformHelper.getPlatformName());
  
  return Container();
}
```

## 🔗 Relacionados
Módulo Pai: [[jxplatform]]
Relacionado: [[JxPlatformType]]
