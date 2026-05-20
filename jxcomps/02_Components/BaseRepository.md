---
modulo: jxcore
tipo: Contrato (jxcore)
status: ✅ Pronto
criado: 2026-04-24
---
# 📖 Módulo: [[jxcore]]

# 🧩 Componente: BaseRepository

## 📝 Descrição
Contrato unificado para a camada de persistência de dados. Padroniza rigorosamente a nomenclatura e as assinaturas dos métodos base de manipulação (CRUD), independentemente de o repositório acessar APIs Rest, Supabase ou bancos locais SQLite.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Retornos Envelopados:** Todos os métodos como `getAll`, `getById`, `save`, `delete` devem retornar obrigatoriamente um envelope de segurança `Future<[[JxResultModel]]<T>>`.
- [x] **Polimorfismo:** Controllers e UseCases nunca devem enxergar implementações concretas (ex: `SupabaseRepository`), mas devem sempre ser tipados e limitados aos métodos deste contrato base.

## 💻 Exemplo de Implementação
```dart
abstract class BaseRepository<T> {
  Future<JxResultModel<List<T>>> getAll();
  Future<JxResultModel<T>> getById(String id);
  Future<JxResultModel<T>> save(T model);
  Future<JxResultModel<bool>> delete(String id);
}
```

## 🔗 Relacionados
Módulo Pai: [[jxcore]]
Relacionado: [[JxResultModel]]
