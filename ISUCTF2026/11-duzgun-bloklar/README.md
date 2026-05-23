# 11. Düzgün Bloklar

**Kategori:** Encoding
**Konu:** Sabit uzunluklu hex blokları ASCII'ye karşılık gelen 2-byte dilimleri olarak çöz.

## Çözüm

Verilen bloklar 4 karakterlik hex parçalarından oluşuyordu:

```
424c
4f43
4b2d
4445
434f
4445
2d33
33
```

Her 4 karakterlik hex blok 2 byte ASCII'ye karşılık gelir:

```
424c -> BL
4f43 -> OC
4b2d -> K-
4445 -> DE
434f -> CO
4445 -> DE
2d33 -> -3
33   -> 3
```

Birleştirilince:

```
BLOCK-DECODE-33
```

## Flag

```
ISUCTF{BLOCK-DECODE-33}
```
