# 29. Seri Numarası

**Kategori:** Tersine Mühendislik
**Konu:** Binary'nin ürettiği token doğrudan flag değil, vault şifresi için KDF girdisi olarak kullanılıyor.

## Çözüm

ZIP'ten iki dosya çıktı:

```
serialcheck
flag_vault.bin
```

Binary çalıştırıldı:

```bash
chmod +x serialcheck
./serialcheck
```

Program seri numarası soruyordu. Farklı denemelerde hep aynı token üretiliyordu:

```
token=serial_state_2026
```

Bu doğrudan flag değildi — vault için KDF girdisiydi.

`flag_vault.bin` içinde Base64 ile saklı `salt` ve `ciphertext` vardı. Çözme mantığı:

```
key    = sha256(salt + "serial_state_2026")
stream = sha256(key + counter)
flag   = ciphertext XOR stream
```

### Çözüm scripti

```python
import json, base64, hashlib

vault = json.load(open("flag_vault.bin"))

salt  = base64.b64decode(vault["salt_b64"])
ct    = base64.b64decode(vault["ciphertext_b64"])

token  = b"serial_state_2026"
key    = hashlib.sha256(salt + token).digest()
stream = hashlib.sha256(key + (0).to_bytes(4, "little")).digest()

flag = bytes(c ^ stream[i] for i, c in enumerate(ct))
print(flag.decode())
```

## Flag

```
ISUCTF{4D3CDY-FXYUHB-TLK8G8}
```
