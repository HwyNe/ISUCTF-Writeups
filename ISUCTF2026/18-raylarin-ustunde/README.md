# 18. Rayların Üstünde — Rail Fence Cipher

**Kategori:** Kriptografi / Klasik Şifre
**Konu:** Rail Fence Cipher; karakterler "ray"lar arasında zigzag yazılır, okuma sırası değiştirilince şifreli metin oluşur.

## Çözüm

Soruda harflerin korunduğu ama sıralarının değiştiği söyleniyordu. İpucu net göndermeydi:

```
Rayların Üstünde — Ray + çit = ne?
```

Bu, **Rail Fence Cipher**'ı işaret ediyordu. Dosyada verilen ciphertext:

```
RFEALEC6IN1
```

Ayrıca metadata:

```
encoding_hint: "the tracks never lie, but the order might"
method: transposition
structure: rows
```

3 raylı Rail Fence ile decode edildiğinde:

```
RAILFENCE61
```

İlk denemede `ISUCTF{RAILFENCE61}` yanlış çıktı — sistem kelimeleri tireli ayrılmış biçimde bekliyordu:

```
RAIL-FENCE-61
```

## Flag

```
ISUCTF{RAIL-FENCE-61}
```
