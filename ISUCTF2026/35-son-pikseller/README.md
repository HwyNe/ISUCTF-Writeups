# 35. Son Pikseller

**Kategori:** Forensics / Steganografi
**Konu:** LSB (Least Significant Bit) farkı — referans ve kanıt görsel karşılaştırılınca düşük bitlerde fark görülür.

## Çözüm

Kanıt görseli ile referans görsel piksel piksel karşılaştırıldı. Fark yalnızca son bitlerde (LSB) görülüyordu.

`image_hashes.txt` dosyasında olay marker'ı vardı:

```
PIKSEL55_son_bitler_konusur
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

`flag_vault.bin` çözülerek elde edildi.
