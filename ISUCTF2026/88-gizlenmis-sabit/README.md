# 88. Gizlenmiş Sabit

**Kategori:** Tersine Mühendislik / Binary Strings
**Konu:** Flag tek string olarak saklanmamış; binary içinde parçalara bölünmüş sabitler concatenation order'a göre birleşiyor.

## Çözüm

```bash
strings const_parts.bin
```

`strings` çıktısında şu sabitler görünüyordu:

```
.LC0: "CONST-"
.LC1: "PART-"
.LC2: "66"
concat_order: LC0+LC1+LC2
```

Concatenation order'a göre parçalar birleştirildi:

```
CONST- + PART- + 66 = CONST-PART-66
```

## Flag

```
ISUCTF{CONST-PART-66}
```
