# 46. Kart Tablosu (Polybius / Grid Lookup)

**Kategori:** Kriptografi / Klasik Şifre
**Konu:** Sayılar row-column şeklinde bir grid'e karşılık geliyor; her sayı tablodan bir karakter çekiyor.

## Çözüm

`numbers.txt` içinde decoy bloklar vardı; esas alınacak kısım "primary sequence" olarak işaretliydi:

```
21 35 23 14 -- 13 32 14 15 -- 61 63
```

Her sayı `row column` (satır sütun) şeklinde okunacaktı. `grid.txt` tablosundan koordinatlar tek tek çözüldü:

```
21 = G
35 = R
23 = I
14 = D

13 = C
32 = O
14 = D
15 = E

61 = 5
63 = 7
```

Bloklar birleştirildiğinde mesaj:

```
GRID CODE 57
```

## Flag

```
ISUCTF{GRID-CODE-57}
```
