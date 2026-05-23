# 67. TLV Firmware

**Kategori:** Embedded / Firmware Analysis
**Konu:** Firmware binary TLV (Type-Length-Value) kayıtları içeriyor; bir kayıt XOR maskelenmiş zlib config.

## Çözüm

Firmware binary tek parça gibi görünse de başında imza vardı:

```
ISUFW3
```

İmzadan sonra TLV kayıtları parse edildi:

```
type=1  length=8   -> BOOTDATA
type=7  length=50  -> masked_zlib_config
type=9  length=5   -> END!!
```

`known_tlv_types.csv` type 7 kaydının `masked_zlib_config` olduğunu söylüyordu.

Type 7 içeriği önce XOR mask ile denenerek açıldı. Tek byte XOR anahtarı:

```
0x5a
```

XOR sonrası veri zlib formatına dönüştü (`78 9c` header) ve `zlib.decompress()` ile açıldı.

Çıkan config:

```json
{"device": "R-900", "marker": "fw_tlv_S2N6"}
```

Solution key olarak marker kullanıldı:

```
fw_tlv_S2N6
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{BVVYV8-E48HGC-LKH6BD}
```
