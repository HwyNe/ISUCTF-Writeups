# 14. Sorgu Satırı

**Kategori:** Forensics / DNS Log Analizi
**Konu:** DNS loglarında normal sorgular arasına sızdırılmış tek anormal kayıt.

## Çözüm

`dns_queries.log` içinde çoğu sorgu normal domain'lerdi (Google, Microsoft, CDN'ler vs.). Aralarında tek farklı görünen kayıt bulundu:

```
dns-row-481.verify.internal.ctf.local
```

Subdomain kısmındaki anlamlı değer doğrudan flag'i veriyordu:

```
DNS-ROW-481
```

## Flag

```
ISUCTF{DNS-ROW-481}
```
