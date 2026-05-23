# 73. Toplu Sorgu (GraphQL Cache Collision)

**Kategori:** Web / GraphQL
**Konu:** Cache key `variables.role`'u dahil etmediği için aynı kullanıcının farklı yetkili sorguları çakışıyor; admin response, normal kullanıcıya servis ediliyor.

## Çözüm

Arşivde GraphQL servis kaynakları, HTTP batch kaydı, log dosyası ve `flag_vault.bin` vardı.

### Cache key analizi

`source/cache.js` içinde cache key üretimi:

```js
operationName + ':' + userId
```

`variables.role` cache key'e dahil edilmiyordu — yani aynı `userId` farklı role'lerle istek attığında cache çakışıyordu.

### Resolver kontrolü

`source/resolver.js`:

```js
if (ctx.role !== 'admin') deny();
```

Normalde admin kontrolü var.

### Saldırı izi

`http/graphql_batch.har` aynı kullanıcıyla batch istek gösteriyordu:

```
Profile     / userId=u77
AdminExport / userId=u77 / variables.role=admin
```

Aynı user içinde önce normal sonra admin sorgu — admin response cache'lendi, sonraki normal isteklerde admin response döndü.

### Marker

`logs/graphql.log` içinde olay marker'ı açıkça verilmişti:

```
cache collision op=AdminExport user=u77 marker=gql_batch_Y2C7
```

Solution key:

```
gql_batch_Y2C7
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{MR9B42-KSG3XW-Q7KCYB}
```
