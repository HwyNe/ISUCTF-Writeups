# 66. Günlükteki Sızıntı

**Kategori:** Forensics / Endpoint + Network Korelasyon
**Konu:** Birden fazla log/CSV'de aynı marker tekrar ediyor; olay zincirinin dosya toplama ve dış bağlantı işareti.

## Çözüm

Arşivdeki dosyalar:

```
endpoint_events.jsonl
network_summary.csv
process_baseline.csv
flag_vault.bin
```

`endpoint_events.jsonl` içinde çok sayıda normal olay arasında tek JSON kayıt dikkat çekiyordu:

```json
{"case": "CASE-022", "marker": "WSORION17_PG9c31a7_archive734"}
```

Aynı marker değeri `network_summary.csv` ve `process_baseline.csv` içinde de tekrar ediyordu:

```
WSORION17_PG9c31a7_archive734
```

Bu değer olay zincirinin dosya toplama + dış bağlantı marker'ı olarak alındı.

`flag_vault.bin` çözüm şeması:

```
kdf:    sha256(salt + solution_key)
cipher: xor-sha256-stream
```

Solution key:

```
WSORION17_PG9c31a7_archive734
```

## Flag

```
ISUCTF{MFWV3Y-PML26U-HKE9N6}
```
