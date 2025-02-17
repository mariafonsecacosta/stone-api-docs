---
title: "Paginação"
date: 2020-05-04T18:32:40-03:00
lastmod: 2020-05-13T18:32:40-03:00
weight: "4"
draft: false
---

Nossas APIs usam um padrão de paginação por cursor. O retorno possui o seguinte formato:

```typescript
{
 cursor: {
 after: string | null,
 before: string | null,
 limit: number
 },
 data: Array&lt;Data&gt;
}
```

Como funciona: deve-se informar o limite de items para a paginação, passando o parâmetro ?limit=10. Na resposta dessa query, será retornado as hashs referente ao cursor no momento da resposta, ex.:
```typescript
{
 cursor: {
 after: ASsa987fqw,
 before: null,
 limit: 10
 },
 data: Array&lt;Data&gt;
}
```

Assim, caso queira consultar o próximo cursor, acrescentar o parâmetro after na chamada: ?limit=10&amp;after=ASsa987fqw, será retornado a próxima paginação.
