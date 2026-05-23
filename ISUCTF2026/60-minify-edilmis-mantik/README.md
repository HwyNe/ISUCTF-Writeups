# 60. Minify Edilmiş Mantık (JavaScript Obfuscation)

**Kategori:** Web / JavaScript Reverse
**Konu:** Minify/obfuscate edilmiş JS dosyası okunması zor olsa da kontrol mantığı içindedir; dizi sabitleri ve transform fonksiyonu çıkarılır.

## Çözüm

`check.min.js` dosyası obfuscated olsa da kontrol mantığı içindeydi.

Dosyada şu dizi bulundu:

```js
["KT", "NJO", "504"]
```

Ardından `_0x1b3c()` fonksiyonu incelendi. Bu fonksiyon her karakterin ASCII değerinden `1` çıkarıyordu:

```
K → J
T → S
N → M
J → I
O → N
```

Bu dönüşüm uygulandığında parçalar çözüldü:

```
KT  → JS
NJO → MIN
504 → 504
```

Program ayrıca formatın `2-3-3` uzunluğunda ve tireli olmasını kontrol ediyordu. Doğru giriş:

```
JS-MIN-504
```

## Flag

```
ISUCTF{JS-MIN-504}
```
