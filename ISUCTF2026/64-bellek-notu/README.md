# 64. Bellek Notu

**Kategori:** Forensics / Memory Strings
**Konu:** Bellek dump'ında residual buffer kalıntısı; çalışmış uygulamadan kalan referans değeri.

## Çözüm

ZIP içinden `memory_strings.raw` dosyası çıkarıldı.

Bellek kesiti üzerinde `strings` analizi:

```bash
strings -a memory_strings.raw
```

Çıktıda normal uygulama bilgileri, ortam değişkenleri ve log kayıtları görüldü. Özellikle residual buffer dump kısmında kalan referans dikkat çekti:

```
-- residual buffer dump @ offset 0x1f40 --
app_ref=MEM-LEFT-808
```

Soru "çalışan uygulamadan kalan bir referans değeri" dediği için olay değeri `app_ref` alanındaki içerikti:

```
MEM-LEFT-808
```

## Flag

```
ISUCTF{MEM-LEFT-808}
```
