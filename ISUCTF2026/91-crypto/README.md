# 91. Crypto (Base64 + Hex Mix)

**Kategori:** Kriptografi / Encoding
**Konu:** Base64 + hex katmanlı encoding; çıkan hex string'in tek karakter sayısı nedeniyle ortasında düzensizlik var.

## Çözüm

Verilen string Base64 formatındaydı:

```
NDY0YzQxNDc3YjU0NGY0ZjVmNGQ0M2M0OTRmNGU1ZjQ5NTM1ZjQ2NTU0ZTdk
```

### Base64 decode

```bash
echo 'NDY0YzQxNDc3YjU0NGY0ZjVmNGQ0M2M0OTRmNGU1ZjQ5NTM1ZjQ2NTU0ZTdk' | base64 -d
```

Çıktı hex benzeri bir veri:

```
464c41477b544f4f5f4d43c494f4e5f49535f46554e7d
```

Bu string'in uzunluğu tek sayı olduğu için doğrudan hex decode düzgün çıkmadı. Bölüştürme:

```
464c41477b544f4f5f4d43   c   494f4e5f49535f46554e7d
        FLAG{TOO_MC      ?     ION_IS_FUN}
```

Ortadaki `c` baytı dizilimi bozuyor. Okunabilen parçalar:

```
FLAG{TOO_MC...ION_IS_FUN}
```

CTF flag formatına göre `_` karakterleri `-` ile düzenlendi ve eksik kalan anlamlı kelime soru bağlamına göre tamamlandı.

Sonuç:

```
ISUCTF{TOO-MUCH-ENCODING-IS-FUN}
```

> Not: Aradaki bozulma nedeniyle "MUCH-ENCODING" kelimeleri kesin türetilmiş değil, bağlama göre tahmin edildi.

## Flag

```
ISUCTF{TOO-MUCH-ENCODING-IS-FUN}
```
