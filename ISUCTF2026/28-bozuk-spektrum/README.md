# 28. Bozuk Spektrum

**Kategori:** Steganografi / Ses Analizi
**Konu:** Stereo ses dosyasında sol/sağ kanal ayrımı yapıldığında, tek kanalla çözülemeyen bilgi diğer kanalda gizlenmiş olabilir.

## Çözüm

Ses dosyası iki kanallıydı. Hint, tek dosyanın yeterli olmadığını söylüyordu.

Arşivdeki `channel_hashes.txt` incelendi — sol/sağ kanal SHA-256 değerleri ve faz bilgileri vardı. Sağ kanal faz analizinden marker çıktı:

```
right_channel_phase34
```

`flag_vault.bin` şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

Solution key olarak marker kullanıldı.

## Flag

`flag_vault.bin` çözülerek elde edildi.
