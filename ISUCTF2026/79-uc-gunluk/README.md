# 79. Üç Günlük (TXN ID Korelasyon)

**Kategori:** Forensics / Multi-Source Log
**Konu:** Aynı işlem üç farklı log dosyasında aynı TXN ID ile takip ediliyor; nihai durum audit log'da.

## Çözüm

Aynı olay üç farklı log dosyasında TXN ID ile takip edildi.

`access.log`:

```
TXN-8821 data commit request
```

`app.log`:

```
TXN-8821 records=606
```

`audit.log`:

```
TXN-8821 user=admin verb=COMMIT result=AUDIT-END-606
```

Aynı işlem admin kullanıcısıyla COMMIT olarak tamamlanmıştı. Final değer audit log'un `result` alanındaydı:

```
AUDIT-END-606
```

## Flag

```
ISUCTF{AUDIT-END-606}
```
