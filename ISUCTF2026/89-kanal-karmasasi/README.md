# 89. Kanal Karmaşası (Channel-Differential LSB)

**Kategori:** Forensics / Steganografi / LSB
**Konu:** İki görsel arasındaki LSB farkı tek bir kanalda taşınıyor; raster bit'leri toplandığında zlib payload çıkıyor.

## Çözüm

Arşivde:

```
reference.png
evidence.png
hashes.txt
flag_vault.bin
```

İki görsel görsel olarak aynıydı. Ancak `reference.png` ile `evidence.png` karşılaştırıldığında yalnızca düşük bit seviyesinde fark vardı.

### XOR analizi

```
diff = reference XOR evidence
```

Farkların özellikle **Green kanalının LSB bitlerinde** olduğu görüldü. Bu LSB bitleri raster sırayla byte'lara çevrilince veri zlib başlığıyla başlıyordu:

```
78 9c
```

`zlib.decompress()` sonrası JSON çıktı:

```json
{"marker": "rgba_zlib_K2M7", "case": "IMG-909"}
```

Solution key:

```
rgba_zlib_K2M7
```

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{JPUFKB-E9XZ4P-WAZUHX}
```
