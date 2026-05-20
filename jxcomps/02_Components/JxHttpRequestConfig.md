---
modulo: jxhttpclient
tipo: Configuração de Rede (jxhttpclient)
status: ✅ Pronto
criado: 2026-04-24
---

# 🌐 Módulo: [[jxhttpclient]]

# 🧩 Componente: JxHttpRequestConfig

## 📝 Descrição
Configuração imutável para requisições HTTP. Encapsula todos os parâmetros necessários (URL, método, headers, body, query e timeout) para realizar uma chamada.

## 🛠️ Diretrizes Obrigatórias (Manual JxComps)
- [x] **Imutabilidade:** Utiliza o método `copyWith` para criar novas instâncias baseadas em configurações existentes.
- [x] **Integração:** Usado estritamente como parâmetro de configuração para o `[[JxHttpClientService]]`.

## 💻 Exemplo de Implementação
```dart
final config = JxHttpRequestConfig(
  url: 'https://api.exemplo.com/v1/dados',
  method: JxHttpMethod.post,
  body: {'chave': 'valor'},
  timeout: Duration(seconds: 15),
);
```

## 🔗 Relacionados
Módulo Pai: [[jxhttpclient]]
Relacionado: [[JxHttpMethod]]

