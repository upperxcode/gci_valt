---

modulo: jxplatform

tipo: Helper (jxplatform)

status: ✅ Pronto

criado: 2026-04-24

---

# 🌐 Módulo: [[jxplatform]]

# 🧩 Componente: JxPermissionHelper

  

## 📝 Descrição

Isola e centraliza a complexidade da negociação de permissões nativas do sistema (Câmera, Localização, Microfone, Armazenamento), usando nativamente a dependência `permission_handler`.

  

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)

- [x] **Solicitação Lazy:** Nunca dispare prompts de permissão no carregamento inicial do aplicativo (splash). Elas devem ser solicitadas apenas no momento em que a feature exata for ativada pelo usuário.

- [x] **Orientação no Fallback:** Retornos falsos devem sempre gerar alertas (`[[JxDialogs]]`) convidativos na interface, orientando o usuário a abrir as configurações do aparelho para liberar a permissão bloqueada caso ele tenha recusado acidentalmente.

  

## 💻 Exemplo de Implementação

```dart

// Momento do clique no botão de "Adicionar Foto"

final granted = await JxPermissionHelper.requestCameraPermission();

  

if (granted) {

abrirCamera();

} else {

JxDialogs.showWarning(

'Precisamos de acesso à câmera para tirar a foto do recibo.'

);

}

```

  

## 🔗 Relacionados

Módulo Pai: [[jxplatform]]