# 41. Zamanlı DNS (DNS Timing Channel)

**Kategori:** Forensics / Covert Channel
**Konu:** DNS sorguları arasındaki zaman farkları (inter-arrival delta) gizli veri taşıyabilir.

## Çözüm

DNS trafiği normal görünse de belirli istemciye ait sorgular incelendi:

```
src   = 10.70.12.44
qname = heartbeat.sync.lab
```

Bu istemcinin ardışık sorguları arasındaki `delta_ms` değerleri iki kümede toplanıyordu:

```
200 ms → 0
700 ms → 1
```

Bu binary stream toplandı:

```
0 0 1 1 0 0 0 1 ...
```

Bit dizisi Base32 alfabesine eşlenince:

```
MRXHGX3UNFWWS3THL5JDQS2R
```

Base32 decode sonucu:

```
dns_timing_R8KQ
```

Bu değer `flag_vault.bin` için solution key olarak kullanıldı.

Vault şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

## Flag

```
ISUCTF{9Z5DMG-QUR2DU-JKTA2M}
```
