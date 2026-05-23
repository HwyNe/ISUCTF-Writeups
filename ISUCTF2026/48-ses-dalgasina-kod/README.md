# 48. Ses Dalgasına Kod

**Kategori:** Steganografi / Ses Analizi
**Konu:** Tek frekanslı tonlar belirli aralıklarla; her ton bir ASCII karaktere karşılık geliyor.

## Çözüm

Ses dosyasında doğrudan konuşma veya strings çıktısı yoktu. Spektrogram incelendiğinde belirli aralıklarla tek frekanslı tonlar görüldü.

Tonların frekansları şu formülle ASCII karaktere dönüştü:

```
ASCII = (frekans - 500) / 13
```

### Örnek çözümler

```
1449 Hz → (1449 - 500) / 13 = 73  → I
1579 Hz → 83 → S
1605 Hz → 85 → U
1371 Hz → 67 → C
1592 Hz → 84 → T
1410 Hz → 70 → F
```

Tüm tonlar okununca:

```
ISUCTF{s3s_sp3ktr0gram}
```

## Flag

```
ISUCTF{s3s_sp3ktr0gram}
```
