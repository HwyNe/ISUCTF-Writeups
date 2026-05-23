# 34. Parça Kontrol

**Kategori:** Tersine Mühendislik
**Konu:** `split_check.py` içindeki her fonksiyon belirli bir index'teki karakteri kontrol ediyor; tüm kontrol fonksiyonları birleştirildiğinde doğru input ortaya çıkar.

## Çözüm

`split_check.py` incelendi. Her fonksiyon `v[i] == 'X'` formatında bir karşılaştırma yapıyordu.

Tüm index/karakter şartları çıkarıldı ve sıraya konuldu:

```
v[0]  = S
v[1]  = P
v[2]  = L
v[3]  = I
v[4]  = T
v[5]  = -
v[6]  = C
v[7]  = H
v[8]  = E
v[9]  = C
v[10] = K
v[11] = -
v[12] = 4
v[13] = 1
```

Birleştirildiğinde:

```
SPLIT-CHECK-41
```

## Flag

```
ISUCTF26{SPLIT-CHECK-41}
```
