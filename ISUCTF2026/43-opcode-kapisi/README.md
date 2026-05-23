# 43. Opcode Kapısı

**Kategori:** Tersine Mühendislik / Custom VM
**Konu:** Doğrulama programı doğrudan string karşılaştırması yapmıyor; ayrı bir `program.vm` bytecode dosyası özel bir VM tarafından yorumlanıyor.

## Çözüm

Arşivde `program.vm` bytecode dosyası vardı. Bytecode başında `ISUVM2` header'ı görüldü. Header'dan sonra gelen veri:

```
41 5a 68 47 56 43 5f 68 7b 00 66 05
```

Bu baytların küçük VM yorumlayıcısı tarafından işlendiği anlaşıldı. Yorumlayıcı mantığı incelendiğinde her baytın `0x37` ile XOR'landığı görüldü.

### Çözüm

```python
data = bytes.fromhex("41 5a 68 47 56 43 5f 68 7b 00 66 05")
print(bytes([b ^ 0x37 for b in data]))
```

Çıkan değer:

```
vm_path_L7Q2
```

Bu değer vault çözme anahtarı olarak kullanıldı. Vault SHA-256 tabanlı stream üretiyordu:

```
derived = sha256(salt + key).digest()
stream  = sha256(derived + counter).digest()
```

## Flag

```
ISUCTF{XJ74CF-HKEU7N-GP5B83}
```
