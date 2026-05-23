# 02. Sembollü Dosya

**Kategori:** Forensics / Dosya Sistemi
**Konu:** Sembolik linkler gerçek dosya gibi görünür ama başka bir hedefe işaret eder.

## Çözüm

`ls -laR` çıktısında `exhibit_a` dosyasının gerçek dosya değil, bir sembolik link olduğu görüldü:

```
exhibit_a -> /opt/case/data/references/ref_74.txt
```

Hedef dosya açıldığında olayla ilişkili değer ortaya çıktı:

```
case_ref: LINK-TARGET-74
```

## Flag

```
ISUCTF{LINK-TARGET-74}
```
