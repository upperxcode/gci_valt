---
tags:
  - manual
  - ia
  - diretrizes
criado: 2026-04-24
---

# 🤖 Manual para Agentes de IA

> **Resumo:** Diretrizes estritas e regras de engajamento para qualquer Inteligência Artificial (ou desenvolvedor humano) operando na base de código do GCI e JxComps. Siga estas regras para manter a consistência arquitetural.

## 📚 Módulos Base (JxComps)

Ao atuar no ecossistema, os agentes devem respeitar a responsabilidade de cada módulo listado no [[GCI_Overview]]:
- **Utilitários Core:** Use [[jxplatform]] para checagens de rede e permissões.
- **UI:** Nunca crie componentes do zero (Material nativo). Use a biblioteca de componentes visuais do [[jxwidgets]].
- **Logs:** Use a classe `JxLog` nativa para saídas de debug, não o `print()`.
- **Contratos:** Utilize [[BaseInterface]] e [[BaseRepository]] de [[jxcore]].

---

## 🛠️ Regras de Implementação

### 1. Detecção de Plataforma e Conectividade
Nunca escreva lógicas cruas utilizando bibliotecas de terceiros na View. Confie no [[jxplatform]]:
```dart
// Correto:
final hasInternet = await JxConnectivityHelper.checkInternetConnection();
if (!hasInternet) throw NoInternetException();

final platform = JxPlatformHelper.getCurrentPlatform();
```

### 2. Permissões de Dispositivo
Toda solicitação de hardware (Câmera, Arquivos) deve passar pelo Helper padronizado:
```dart
final cameraGranted = await JxPermissionHelper.requestCameraPermission();
if (!cameraGranted) throw PermissionDeniedException('Camera');
```

### 3. Comunicação HTTP (Requisições)
Evite instanciar o `http` ou `dio` soltos. Utilize o serviço encapsulado de HTTP do sistema:
```dart
final config = JxHttpRequestConfig(
  url: '/api/itens',
  method: JxHttpMethod.get,
  queryParameters: {'pagina': 1},
);

final result = await httpClient.request<ItemList>(
  config: config,
  parser: (data) => ItemList.fromJson(data),
);

if (!result.isSuccess) {
  JxLog.error('Falha na requisição', error: result.message);
}
```

### 4. Acesso a Dados e Repositórios
Sempre que o agente precisar recuperar ou armazenar dados locais/remotos para o domínio do GCI (ex: [[PessoaModel]]), ele **deve** implementar as interfaces base do `jxcore`:
```dart
class CondominioRepository implements BaseRepository<CondominioModel> {
  @override
  Future<void> save(CondominioModel entity) async { /* ... */ }
  
  @override
  Future<CondominioModel?> findById(String id) async { /* ... */ }
}
```

### 5. Retornos Inflexíveis (`JxResultModel`)
**Atenção:** Em nenhuma hipótese um repositório ou serviço deve vazar *Exceptions* para a camada de Interface de Usuário. Todo tratamento de erro se dá embrulhado em um modelo de resultado (ver [[JxResultModel]]):
```dart
// SEMPRE verifique o status de sucesso.
if (result.isSuccess) {
  // Faça algo com result.data
} else {
  // Trate utilizando result.message
}
```

### 6. Testes Unitários e Mocking (Supabase)
Para testar Controllers que dependem do Supabase, **nunca** utilize o cliente real. Siga o padrão de Mocking Robusto estabelecido:

1. **Injeção via GetIt:** Certifique-se de que o `SupabaseDataSource` recebe o cliente via `GetIt.I<SupabaseClient>()`.
2. **Double Mock Pattern:** Utilize classes especializadas para mockar a API fluente (Chained API):
```dart
// Mock para retornos de Lista
class MockFilterList extends Mock implements PostgrestFilterBuilder<List<Map<String, dynamic>>> {
  final List<Map<String, dynamic>> data;
  MockFilterList(this.data);
  @override
  Future<R> then<R>(FutureOr<R> Function(List<Map<String, dynamic>>) onValue, {Function? onError}) {
    return Future.value(onValue(data));
  }
}

// Mock para retornos de Objeto Único (maybeSingle)
class MockFilterMap extends Mock implements PostgrestFilterBuilder<Map<String, dynamic>?> {
  final Map<String, dynamic>? data;
  MockFilterMap(this.data);
  @override
  Future<R> then<R>(FutureOr<R> Function(Map<String, dynamic>?) onValue, {Function? onError}) {
    return Future.value(onValue(data));
  }
}
```
3. **Stubs Obrigatórios:** Sempre use `thenAnswer((_) => mockFilter)` em vez de `thenReturn`, pois o Mocktail identifica o método `.then` da API do Postgrest e exige um retorno assíncrono/thenable.

---
**Páginas Relacionadas:**
- [[GCI_Overview]] - Volte para a documentação raiz.
