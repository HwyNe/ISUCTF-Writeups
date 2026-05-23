# 76. Bellekteki Anahtar

**Kategori:** Forensics / Memory / Record Parsing
**Konu:** Bellek dump'ı özel kayıt formatına sahip (`REC0` header + uint32 pid + ASCII payload); normal `strings` gürültülü, parse etmek gerekir.

## Çözüm

Normal `strings` çıktısı çok gürültülü. `format_hint.txt` okundu:

```
record header: REC0, pid:uint32 little-endian, ascii payload follows
```

`memdump.lite` içinde `REC0` kayıtları arandı. Kayıtlar parse edildi.

Gürültü kayıtları arasında kritik kayıt:

```
pid    = 4312
proc   = agent
socket = 203.0.113.77:9443
clip   = memsock_E4H7
```

`network_baseline.csv` bu socket'in normal olmadığını doğruluyordu:

```
203.0.113.77:9443,no
```

Solution key:

```
memsock_E4H7
```

## Flag

```
ISUCTF{TGSZ99-SQCAN7-NK7B8N}
```
