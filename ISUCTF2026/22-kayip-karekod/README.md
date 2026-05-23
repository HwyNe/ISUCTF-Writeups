# 22. Kayıp Karekod

**Kategori:** Forensics / Steganografi / Polyglot
**Konu:** Yanlış isimlendirilmiş dosya gerçek türünde değil; içinde gömülü başka bir format saklı.

## Çözüm

ZIP açıldığında şu dosyalar vardı:

```
kanit_paketi.tar.gz
analist_notu.pdf
arsiv_bildirimi.txt
flag_vault.bin
```

### Adım 1 — Yanlış uzantı

`file kanit_paketi.tar.gz` çıktısı: aslında PNG.

### Adım 2 — Gömülü ZIP

PNG sonunda `PK\x03\x04` imzası bulundu — sonda gömülü ZIP.

```bash
binwalk kanit_paketi.tar.gz
dd if=kanit_paketi.tar.gz of=embedded.zip bs=1 skip=<offset>
```

### Adım 3 — ZIP parolası

ZIP parolalıydı. `analist_notu.pdf` içindeki gizli metin:

```
ars-1947
```

### Adım 4 — QR kod

ZIP'ten `karekod_parcasi.png` çıktı. QR okuyucu ile:

```
ARS-1947 dogrulandi. son belirtec: gorsel-isaret-713
```

### Adım 5 — Solution key

```
1947_gorsel_isaret_713
```

`flag_vault.bin` bu anahtarla çözüldü.

## Flag

`flag_vault.bin` çözülerek elde edildi.
