# 27. Boğaz Sinyali (Bosphorus Signal)

**Kategori:** Steganografi / OSINT
**Konu:** Flag dosya metadata'sında veya gömülü yorum alanında saklı.

## Çözüm

`kizkulesi.jpg` dosyası `strings` ve `exiftool` ile incelendi:

```bash
strings kizkulesi.jpg
exiftool kizkulesi.jpg
```

Dosya comment alanında doğrudan flag bulundu:

```
comment: "ISUCTF{NIGHT_SIGNAL_BOSPHORUS}"
```

## Flag

```
ISUCTF{NIGHT_SIGNAL_BOSPHORUS}
```
