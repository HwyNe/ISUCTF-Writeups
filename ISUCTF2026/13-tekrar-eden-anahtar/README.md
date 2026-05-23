# 13. Tekrar Eden Anahtar

**Kategori:** Kriptografi / XOR Reuse
**Konu:** Aynı keystream ile XOR'lanmış iki ciphertext varsa, iki şifreli metnin XOR'u keystream'i yok eder; crib-dragging ile mesajlar okunabilir.

## Çözüm

İki ciphertext aynı keystream ile XOR'lanmıştı:

```
C1 = P1 XOR K
C2 = P2 XOR K
```

İki ciphertext XOR'landığında:

```
C1 XOR C2 = P1 XOR P2
```

Mesajlardan birinin başlangıcı tahmin edilebilirdi:

```
STATUS: OPERATIONAL
```

Bu crib mesaj XOR sonucuna kaydırılarak (crib-dragging) diğer mesaj okundu:

```
REF: XOR-REUSE-404
```

## Flag

```
ISUCTF{XOR-REUSE-404}
```
