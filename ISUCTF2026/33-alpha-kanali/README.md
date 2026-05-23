# 33. Alpha Kanalı

**Kategori:** Forensics / Steganografi
**Konu:** Yanıltıcı uzantı — `.png` dosyası aslında ASCII log dosyası.

## Çözüm

`logo.png` dosyası `file` komutuyla incelendiğinde PNG değil ASCII metin olduğu görüldü.

İçinde çok sayıda `NOISE` kaydı vardı. Bu kayıtlar filtrelendiğinde gerçek marker görüldü:

```
alpha_layer_render33
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

`flag_vault.bin` çözülerek elde edildi.
