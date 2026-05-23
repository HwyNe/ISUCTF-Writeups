# 10. Tekrar Eden Nonce

**Kategori:** Kriptografi / Nonce Reuse
**Konu:** Stream cipher veya AEAD'de aynı nonce iki kez kullanılırsa keystream XOR'u plaintext'i sızdırır.

## Çözüm

API loglarında aynı kullanıcıya ait iki şifreli yanıtın aynı nonce ile üretildiği görüldü.

Aynı keystream:

```
C1 = P1 XOR K
C2 = P2 XOR K
C1 XOR C2 = P1 XOR P2
```

İki ciphertext XOR'landığında keystream düşer. Tahmin edilebilir JSON yapısıyla (mesaj başlıkları, alan adları) crib-dragging yapılarak diğer mesaj okundu. `schema_reference.json` içinde `token_hint` olarak da geçen marker:

```
u17_nonce_reuse_secret
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

## Flag

```
ISUCTF{AKV37C-WQVUDM-T2LSBS}
```
