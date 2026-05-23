# 17. Parça Parça

**Kategori:** Forensics / Dosya Kurtarma
**Konu:** Parçalara bölünmüş bir dosya, doğru sırada birleştirilince geçerli bir format oluşturur.

## Çözüm

Arşivden çıkan dosyalar:

```
chunk01.dat
chunk02.dat
chunk03.dat
hint.txt
```

`hint.txt` parçaların sırasını veriyordu:

```
01 → 02 → 03
```

Her chunk dosyasında binary veri etiketler arasında saklıydı:

```
# BEGIN_BINARY
...
# END_BINARY
```

Üç binary parça sırasıyla birleştirildiğinde geçerli bir PNG oluştu. PNG açıldığında içindeki değer görüldü:

```
CHUNK-END-602
```

## Flag

```
ISUCTF{CHUNK-END-602}
```
