# 54. Yanlış Etiket

**Kategori:** Forensics / Polyglot / File Carving
**Konu:** Yanlış uzantı + gömülü ZIP — `.log` görünümlü dosya sonunda PK imzası taşıyor.

## Çözüm

`export_2026.log` dosyasının sonunda gömülü ZIP imzası bulundu:

```bash
binwalk export_2026.log
strings export_2026.log | grep "PK"
```

PK ZIP imzası tespit edildi. Gömülü ZIP çıkarıldı:

```bash
dd if=export_2026.log of=embedded.zip bs=1 skip=<offset>
unzip embedded.zip
```

İçinde `metadata.txt` vardı. Token ve case bilgisi normalize edildi:

```
YAN-2226 + etiket_offset_74
```

Solution key:

```
YAN2226_etiket_offset_74
```

`flag_vault.bin` bu anahtarla çözüldü.

## Flag

`flag_vault.bin` çözülerek elde edildi.
