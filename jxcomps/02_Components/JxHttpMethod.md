---
modulo: jxhttpclient
tipo: Enum e Extensões (jxhttpclient)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxhttpclient]]

# 🧩 Componente: JxHttpMethod

## 📝 Descrição
Enumeração que padroniza os métodos HTTP suportados pela camada de rede (GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS).

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Padronização:** Garante uso seguro tipado ao invés de Strings cruas para definição do método.
- [x] **Extensões Úteis:** Fornece as propriedades `isIdempotent` e `isSafe` para facilitar a validação em regras de negócio de cache ou retry.

## 💻 Exemplo de Implementação
```dart
final metodo = JxHttpMethod.get;
if (metodo.isSafe) {
  // Pode ser repetido com segurança sem causar efeitos colaterais
}
```

## 🔗 Relacionados
Módulo Pai: [[jxhttpclient]]
Relacionado: [[JxHttpRequestConfig]]

