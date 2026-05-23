# 50. Günlük Kalıntısı

**Kategori:** Forensics / Disk Carving
**Konu:** Disk image'in partition offset bölgesinde unutulmuş token; `strings` ile çıkarılabiliyor.

## Çözüm

ZIP içinde:

```
disk_image.dd
flag_vault.bin
journal_hashes.csv
```

Disk image'e `strings` uygulandı:

```bash
strings disk_image.dd | grep -i "token\|case\|JNL"
```

Partition offset bölgesinde unutulmuş bir kayıt çıktı:

```
token=journal_carve_B9K2;case=JNL-602
```

`flag_vault.bin` XOR-SHA256 stream cipher kullanıyordu. KDF şeması:

```
sha256(salt + solution_key)
```

Solution key:

```
journal_carve_B9K2
```

Decrypt edildiğinde flag elde edildi.

## Flag

```
ISUCTF{N2B5EW-2BKY3W-GNKJTK}
```
