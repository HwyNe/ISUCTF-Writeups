# 55. Bytecode Grafı

**Kategori:** Tersine Mühendislik / Python Bytecode
**Konu:** Kaynak kod yok, `validator.pyc` bytecode'undan kontrol mantığı çıkarılıyor.

## Çözüm

Arşivdeki dosyalar:

```
validator.pyc
failed_inputs.txt
runtime_note.json
flag_vault.bin
```

`runtime_note.json` giriş fonksiyonunun `check(path)` olduğunu söylüyordu.

`validator.pyc` Python disassembly (örn. `dis`, `uncompyle6`, `decompile3`) ile incelendi:

```bash
python3 -m dis validator.pyc
```

`check` fonksiyonu şu karşılaştırmayı yapıyordu:

```python
path == "A7-C2-F9-K4"
```

Doğru input verildiğinde fonksiyon belirteci döndürüyordu:

```
pyc_graph_Z4M8
```

`failed_inputs.txt` dosyasındaki başarısız denemeler doğru yolun `A7-C2-F9-K4` olduğunu doğruluyordu:

```
A7-C2-F9
A7-C2-K4
A7-F9-K4
```

`flag_vault.bin` vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

Solution key olarak bytecode çıktısı kullanıldı:

```
pyc_graph_Z4M8
```

## Flag

```
ISUCTF{AQZA7M-LCN39A-JE2FMZ}
```
