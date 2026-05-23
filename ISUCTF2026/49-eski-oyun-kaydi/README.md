# 49. Eski Oyun Kaydı

**Kategori:** Forensics / Binary
**Konu:** Binary kayıt dosyası içinde gömülü marker.

## Çözüm

Binary oyun kaydı dosyaları `strings` ile incelendi:

```bash
strings oyun_kaydi.bin | grep -i "case\|marker"
```

Çıktıda:

```
CASE-015:oyun_kaydi_cozuldu
```

Solution key olarak token kullanıldı:

```
oyun_kaydi_cozuldu
```

`flag_vault.bin` çözüldü.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

`flag_vault.bin` çözülerek elde edildi.
