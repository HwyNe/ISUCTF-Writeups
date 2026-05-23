# 04. Silinmiş Gibi

**Kategori:** Forensics / Arşiv Analizi
**Konu:** Arşiv içindeki nokta ile başlayan gizli dosyalar `ls` ile görünmez ama oradadır.

## Çözüm

ZIP açıldı, gizli dosyalar listelendi:

```bash
unzip arsiv.zip
ls -la
```

Normal dosyaların yanında bir gizli dosya gözüktü:

```
.metadata_cache
```

İçeriği doğrudan flag'i veriyordu:

```
trace_code: ZIP-TRACE-512
flag: ISUCTF{ZIP-TRACE-512}
```

## Flag

```
ISUCTF{ZIP-TRACE-512}
```
