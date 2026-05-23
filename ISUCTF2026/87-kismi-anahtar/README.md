# 87. Kısmi Anahtar (Vigenère + Known Format)

**Kategori:** Kriptografi / Vigenère
**Konu:** Anahtarın bir kısmı biliniyor; format ipucu (WORD-WORD-NN) ile eksik karakterler tamamlanıyor.

## Çözüm

Şifreleme Vigenère tarzı. Anahtar uzunluğu 6 ve ilk 3 karakter verilmiş:

```
key_known = ISU???
```

Ciphertext:

```
XSLVBFT-CYA-508
```

### İlk 3 karakter

```
X - I = P
S - S = A
L - U = R
```

Plaintext `PAR...` ile başlıyor. Format ipucu `WORD-WORD-NN` dediği için ilk kelime muhtemelen:

```
PARTIAL
```

### Eksik anahtar karakterleri

```
V - T = C
B - I = T
F - A = F
```

Anahtar tamamlanıyor:

```
ISUCTF
```

### Tüm ciphertext

Anahtarla çözüldüğünde:

```
PARTIAL-KEY-508
```

## Flag

```
ISUCTF{PARTIAL-KEY-508}
```
