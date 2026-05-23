# 12. Katmanlı Zarf

**Kategori:** Kriptografi / Encoding
**Konu:** Mesaj birden fazla dönüşüm katmanı altında saklanmış; her katman sırayla soyulmalı.

## Çözüm

`envelope.txt` içindeki payload:

```
OTZENjc3RTE0MUYxNzdGMUEwNTE2MUYxQzA0MUYx
```

`hint.txt` katman sırasını veriyordu:

```
base64 → reverse → hex decode → XOR (key: 'Z' = 0x5a)
```

Dıştan içe doğru çözüm:

1. **base64 decode** → `96D677E141F177F1A05161F1C041F1`
2. **reverse** → `1F140C1F16150A1F771F141E776D69`
3. **hex decode** → ham byte dizisi
4. **XOR 0x5a** → düz metin

Sonuç:

```
ENVELOPE-END-73
```

## Flag

```
ISUCTF{ENVELOPE-END-73}
```
