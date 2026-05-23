# 63. Bytecode Notu (PYC Reverse)

**Kategori:** Tersine Mühendislik / Python Bytecode
**Konu:** Kaynak kod yok; `.pyc` dosyası doğrudan bytecode olarak incelenir.

## Çözüm

İlk olarak dosya türü kontrol edildi:

```bash
file checker.pyc
```

Çıktı:

```
Byte-compiled Python module for CPython 3.12
```

Bu yüzden `pyinstxtractor` kullanılmadı — dosya PyInstaller arşivi değil, doğrudan `.pyc`'di.

`strings` ve bytecode sabitleri incelendiğinde şu parçalar görüldü:

```
PYC
RECOVER
QXBSDBNWDS
cc0
```

`QXBSDBNWDS` değeri karakterlere `xor 1` uygulanınca:

```
PYCRECOVER
```

Programın beklediği format:

```
PYC-RECOVER-??
```

Hash kontrolü doğru son değerin `95` olduğunu doğruladı.

Doğru giriş:

```
PYC-RECOVER-95
```

## Flag

```
ISUCTF{PYC-RECOVER-95}
```
