# 78. Gömülü Arşiv

**Kategori:** Forensics / Polyglot / File Carving
**Konu:** PNG dosyasının sonuna ZIP gömülmüş; `binwalk` ile tespit edilip `dd` ile çıkarılıyor.

## Çözüm

```bash
binwalk poster_final.png
```

PNG dosyasının sonunda gömülü ZIP tespit edildi (offset `31486`).

```bash
dd if=poster_final.png of=embedded.zip bs=1 skip=31486
unzip embedded.zip
cat metadata/internal_ref.txt
```

`internal_ref.txt` dosyasında flag/referans değeri vardı.

## Flag

Gömülü ZIP'ten çıkarılan dosyadan elde edildi.
