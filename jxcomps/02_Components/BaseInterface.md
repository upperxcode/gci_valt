---
modulo: jxcore
tipo: Contrato (jxcore2)
status: ✅ Pronto
criado: 2026-04-24
---


# 📖 Módulo: [[jxcore]]

# 🧩 Componente: BaseInterface

## 📝 Descrição

Contrato arquitetural genérico para a fundação de serviços, controllers e managers. Tem como principal objetivo garantir que os componentes possuam um ciclo de vida padronizado de inicialização e descarte na injeção de dependências.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)

- [x] **Lifecycle Controlado:** Obriga a implementação do método `init()` para centralizar inicializações complexas ou assíncronas que não devem ser alocadas no construtor padrão.

- [x] **Prevenção de Leaks:** Exige a presença do método `dispose()` para liberação de memória, cancelamento de streams e limpeza de listeners, fundamental ao lidar com containers como GetIt ou Provider.

  

## 💻 Exemplo de Implementação

```dart

abstract class IMeuServico implements BaseInterface {

Future<void> sincronizarDados();

}

  

class MeuServico implements IMeuServico {

@override

void init() {

// Escutar streams do websocket

}

  

@override

void dispose() {

// Cancelar timers e streams

}

@override

Future<void> sincronizarDados() async {}

}

```

  

## 🔗 Relacionados

Módulo Pai: [[jxcore]]
